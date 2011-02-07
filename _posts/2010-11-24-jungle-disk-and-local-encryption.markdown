--- 
layout: post
title: Jungle Disk & Local Encryption
tags: 
- linux
- internet
- jungle disk
- kde
- backup
---
For the past several years I have used <a href="https://s3.amazonaws.com/">Amazon S3</a> in conjunction with <a href="http://www.jungledisk.com/">Jungle Disk</a> to perform painless online backups. Luckily, I jumped on the Jungle Disk bandwagon back when they offered a "Lifetime" pricing option which cost $20. In 2008 when they introduced the Plus service, which enabled web access, incremental changes, and upload resume for $1/mo, I jumped on it and have been a Plus subscriber ever since. 

Why do I prefer Jungle Disk over the many other <a href="http://en.wikipedia.org/wiki/Comparison_of_online_backup_services" title="Comparison of online backup services">online other backup tools</a>? It is rather simple: I own my data. With Jungle Disk, my data is stored on S3 buckets associated with <em>my</em> Amazon AWS credentials. Moreover, Jungle Disk has released an <a href="http://downloads.jungledisk.com/jungledisk/JungleDiskSourceExample.zip" title="Jungle Disk Source Example">example open source client</a> that can be used to download and decrypt data uploaded and ecrypted with Jungle Disk.

Sure, I could rig up a commensurate system for free using <a href="http://code.google.com/p/s3fs/" title="s3fs: FUSE-based file system backed by Amazon S3">s3fs</a> and rsync. However, I would rather save my valuable time and rely on the experts at Jungle Disk whose livelihood is making this software work, and work well.

Jungle Disk has a Drop Box-esque feature called <a href="http://support.jungledisk.com/forums/61795/entries/74380" title="Jungle Disk: Sync Folders">Sync Folders</a> which allows you to keep a local folder synchronized with a folder on your network drive. I use this feature heavily to keep work and school files synced between my laptop and desktop.

My one gripe with Sync Folders is that it does not encrypt locally stored data. I would like a solution whereby locally stored data is encrypted, yet Jungle Disk can still backup and sync the decrypted data.

For unrelated reasons I prefer <a href="http://www.arg0.net/encfs" title=" EncFS Encrypted Filesystem">encfs</a> over Truecrypt, so I devised a solution that decrypts an encfs filesystem to a mount point that Jungle Disk is set to use, though it can be modified to accommodate Truecrypt. For this to function properly the encfs fs must be decrypted and mounted before Jungle Disk is started, else Jungle Disk will begin cheerfully downloading the remote data into the empty mount point.

Here is the bash script that does just that. It uses kdialog to prompt for the encryption key, then attempts to decrypt and mount the fs, and if successful starts Jungle Disk. I added it as a script to Autostart in KDE's system settings.

{% highlight bash %}
#!/bin/bash

## Config ##

JD=$HOME/bin/junglediskdesktop/junglediskdesktop

ENCFS=/usr/bin/encfs
ENCFS_ROOTDIR=$HOME/docs/.private/
ENCFS_MNTPOINT=$HOME/docs/private_enc

DIALOG=/usr/bin/kdialog
#DIALOG=/usr/bin/Xdialog
#DIALOG=/usr/bin/zenity

## Do not edit below ##

KEY=$($DIALOG --title "Start Encrypted Jungle Disk" --password "Input key to decrypt $ENCFS_ROOTDIR. Jungle Disk will be started following a successful mount.")
if [ $? != 0 ]; then
  # user pressed cancel
  exit
fi

echo $KEY | $ENCFS --stdinpass $ENCFS_ROOTDIR $ENCFS_MNTPOINT
if [ $? != 0 ]; then
  $DIALOG --title "Mount Failed" --msgbox "The mount of $ENCFS_MNTPOINT failed. Aborting Jungle Disk start." 0x0
  exit
fi

#start JD

$JD &
{% endhighlight %}
