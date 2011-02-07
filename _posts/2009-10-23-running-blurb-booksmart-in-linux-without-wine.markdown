---
layout: post
title: Running Blurb Booksmart in Linux (without Wine)
tags:
- ubuntu
- blurb
---

<div class='stb-info_box'>
Update: 2009.12.20. New version of installer released with major bugfixes. <br/>
Update: 2010.11.06. Fixed download link.
</div>
Blurb Booksmart is a book layouting application from <a href="http://www.blurb.com">Blurb Inc.</a> that enables budding authors to create books using their own text and images. Think of it as a highly specialized Adobe Illustrator or Microsoft Publisher. After creating your book in the software, you upload it to Blurb's website where you can then order printed copies of the book.

Officially, Blurb supports Booksmart only on Windows and Mac, however it is a generic Java application, and as such can easily be ran on Linux - with some finagling. You could try and run it through wine, but the layer of emulated Windows on top of the Java makes for an annoyingly sluggish experience.  To make it easier for others, I've created a little script that will automatically download, convert, and install Booksmart in Linux.

<div class='stb-info_box'>
Note: While, the following instructions are Ubuntu specific, a determined other-distro user could replace the <em>apt </em> calls in the script with calls to the appropriate package management tool.
</div>

<div class="stb-download_box" style="background-image: url(http://www.binaryelysium.com/blog/wp-content/plugins/wp-special-textboxes/images/download-b.png); min-height: 40px; padding-left: 50px; "><br>
<strong><a href="http://binaryelysium.com/code/Blurb_Booksmart_Installer-0.2.tar.gz">Blurb Booksmart Installer</a></strong><br>
Author: <a href="http://www.binaryelysium.com">Ramblurr</a>, version: 0.2, updated: December 12, 2009,<br>
Requires Java Version 1.6 or higher, Ubuntu Linux.</div>

<h3>Setting up the Location</h3>
After downloading the package, open up a terminal, and then extract the contents of the tarball.

{% highlight bash %}
tar zxf Blurb_Booksmart_Installer-0.2.tar.gz
{% endhighlight %}

Change to the directory where you want booksmart installed, and copy <em>install.sh</em> to that location.
{% highlight bash %}
Example:
cd /home/username/bin/
cp /path/to/Blurb_Booksmart_Installer/install.sh .
{% endhighlight %}

<h3>Run the Installer</h3>
With the terminal still open to the location where you want booksmart installed, execute the install script. Don't forget to give it executable permissions first.
{% highlight bash %}
chmod +x install.sh
./install.sh
{% endhighlight %}
It will download all the necessary files to install booksmart 2.5.1. The process might take awhile on a slow internet connection.

<h3>Edit the launcher script </h3>
Once the script has finished executing, Booksmart should be installed in the current directory. You'll need to edit the launcher script, so it knows where Booksmart is. The launcher script is <em>booksmart.sh</em> in the tarball.

Open it in an editor and edit the second line to point to the directory you created in step slash booksmart.
{% highlight bash %}
Example: BOOKSMART_PATH=/home/username/bin/booksmart
{% endhighlight %}
You can put this launcher script anywhere and use it to start bookmark. Don't forget to give it executable permissions.

By default, Booksmart saves its data in $HOME/My Documents if you don't like this you can change it by opening Booksmart and running File > Change Data Location.

<a href="http://www.binaryelysium.com/blog/wp-content/uploads/2009/10/booksmart_linux.png" title="Booksmart running in Kubuntu" rel="lightbox"><img src="http://www.binaryelysium.com/blog/wp-content/uploads/2009/10/booksmart_linux-300x187.png" alt="Booksmart running in Kubuntu" title="Booksmart running in Linux" width="300" height="187" class="size-medium wp-image-156" /></a>

Happy Blurbing : )
