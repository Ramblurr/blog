--- 
layout: post
title: GSoC Report Week 4
tags: 
- gsoc
- amarok
- mp3tunes
---
<h4>Project: <a href="http://www.mp3tunes.com">MP3tunes</a> + <a href="http://www.amarok.kde.org">Amarok</a> Integration</h4><span style="font-size:8pt">Total Commits: <a href="http://kollide.net:8060/changelog/~author=link/Amarok" title="All my Amarok commits">84</a> Weekly Commits: 36</span><h4><a name="past">Past 7 Days</a></h4>Starting these posts with "It was another busy week.." is starting to get boring; I'll cook up something more exciting for next week.

In case you missed it, in the past seven days <a href="http://binaryelysium.com/blog/2008/06/20/one-small-step-for-amarok/">history has been made</a>. I'll let that stand in as the bulk of my weekly report, but a few worthwhile things have occurred since then that deserve a mention.

Remote Track Upload - You can now sideload tracks to your MP3tunes collection from remote sources in Amarok. What the heck is sideload and what remote sources you ask? Sideload is a feature of the MP3tunes API that allows for server-to-server transfers. This means you can give your Locker a URL to a track, and it will automatically be downloaded into your Locker. Currently Amarok sports three services with remote collections that are sideloadable to MP3tunes: Ampache, Magnatune, and Jamendo. This method of transferring is generally very fast, because the transfer bypasses your slow internet connection.

Upload Progress Bar - When you upload (or sideload) tracks to MP3tunes there is now a simple status bar to let you know how far along in the process you are. 

Non-Supported Track Filtering - This one is simple: If you try and upload a file-type that MP3tunes doesn't support, Amarok will tell you and stop that track from being transferred.<h4><a name="upcoming">Upcoming 7 Days</a></h4>
<ul>	<li>Work on allowing MP3tunes tracks to persist after a restart.</li>	<li>Flesh out the synchronization system: what it's going to do, and how it's going to do it.</li>	<li>Design any UI widgets needed for the syncing system</li></ul>

The first one will be simple, in fact I plan to code it up after writing this report. These second and third tasks, however, signify that I'm moving into the last stage of the project. According to my original proposal I am ahead by a week, so I'll be using this week as extra time to plan and get a jump-start on the synchronization framework.





