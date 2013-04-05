--- 
layout: post
title: One small step for Amarok...
tags: 
- gsoc
- amarok
- mp3tunes
---
I'm very excited to announce that the first Amarok->Cloud transfer has taken place. Just moments ago, for the first time ever (as far as I'm aware), a track was sent up into the Cloud from a desktop media player, escaping the local collection prison. This track shed the chains of limited accessibility, and is no longer doomed to obscurity, lost in an sql database in my home directory.

This lucky track happened to be <a href="http://www.last.fm/music/Brad+Sucks/_/Making+Me+Nervous" title="Making Me Nervous">Making Me Nervous</a> by <a href="http://www.magnatune.com/artists/brad_sucks" title="Brad Sucks">Brad Sucks</a> available over at the great indie music label <a href="http://www.magnatune.com" title="Magnatune: Independent Music">Magnatune</a>.

<div style="width: 220; text-align: center;"><object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=7,0,0,0" width="220" height="15" ><param name="allowScriptAccess" value="sameDomain"/><param name="movie" value="http://embed.magnatune.com/img/magnatune_player_embedded_single.swf?playlist_url=http://embed.magnatune.com/artists/albums/bradsucks-dontknow/hifi.xspf&autoload=true&autoplay=&playlist_title=I%20Dont%20Know%20What%20Im%20Doing%20:%20Brad%20Sucks"/><param name="quality" value="high"/><param name="bgcolor" value="#E6E6E6"/><embed src="http://embed.magnatune.com/img/magnatune_player_embedded_single.swf?playlist_url=http://embed.magnatune.com/artists/albums/bradsucks-dontknow/hifi.xspf&autoload=true&autoplay=&playlist_title=I%20Dont%20Know%20What%20Im%20Doing%20:%20Brad%20Sucks" quality="high" bgcolor="#E6E6E6" name="xspf_player" allowscriptaccess="sameDomain" type="application/x-shockwave-flash" pluginspage="http://www.macromedia.com/go/getflashplayer" align="center" height="15" width="220"> </embed></object><FONT FACE="Verdana, Arial, utopia, sans-serif" SIZE="1" COLOR="#000000"><br><a href="http://magnatune.com/artists/albums/bradsucks-dontknow"><b>I Dont Know What Im Doing</b></a> by <a href="http://magnatune.com/artists/brad_sucks"><b>Brad Sucks</b></a></font></div>


Early this morning I <a href="http://kollide.net:8060/changelog/~author=link/Amarok/?cs=15470">committed</a> the last bit of code that allows you to upload tracks to your <a href="http://www.mp3tunes.com/">MP3tunes Locker</a> from Amarok. Amarok is the first client, besides the official client, to allow you to do such a thing. One of the great things about this feature is it's seamless integration in the UI.


<a href='http://binaryelysium.com/images/amarokCopyToMp3tunes.png'>Click for the full view
<img src="http://binaryelysium.com/blog/wp-content/uploads/2008/06/amarokcopytomp3tunes-300x170.png" alt="Amarok 2: Copy to Mp3tunes" title="Amarok 2: Copy to Mp3tunes" width="300" height="170" class="aligncenter size-medium wp-image-28" /></a>

After a short upload I go check the MP3tunes Web Player
<a href='http://binaryelysium.com/images/mp3tunesBrad.png'><img src="http://binaryelysium.com/blog/wp-content/uploads/2008/06/mp3tunesbrad-300x229.png" alt="Listening to Brad Sucks via MP3tunes" title="Listening to Brad Sucks via MP3tunes" width="300" height="229" class="alignnone size-medium wp-image-29" /></a>

From this point I can listen to the track on my phone, on my squeezebox, or any other <a href="http://www.mp3tunes.com/partner/cb/partnerlist">MP3tunes supported devices</a>.

Of course there are some caveats, but I aim to fix these over the next several days:
<ul>	<li>No upload progress information.</li>	<li>No error handling when you attempt to upload a filetype mp3tunes doesn't support.</li>	<li>It's not possible to upload non-local content (say from magnatune or ampache)</li></ul>

Don't start thinking that things are winding down; uploading and downloading are only one small part of the show. The end goal is <em>fully automated bi-directional syncing</em> between Amarok and MP3tunes with 100% support for the MP3tunes API.

What exactly does this entail? 

<ol>
	<li>I foresee a "keep in sync with MP3tunes" checkbox for each playlist in the Amarok playlist browser, so you can add/remove tracks from your favorite playlists and thoughtlessly have access to them on any MP3tunes enabled device. </li>
	<li>Imagine clicking "Purchase" at an online music store (like <a href="http://www.eclassical.com/">eclassical</a>) and having the tracks instantly available in Amarok and anywhere else you have access to your locker.</li>
	<li>Your friend beams you a track from his Android phone to your Android phone while you are out on the town, and when you get home the track is all ready in your local Amarok collection,  added to your smart playlists ready to jam.</li>	
            <li>You subscribe to an awesome podcast using Amarok's built in podcast directory, and seconds after a new episode is released it's available on your wifi enabled portable player (or phone)  </li>
</ol>

And it all started today.
