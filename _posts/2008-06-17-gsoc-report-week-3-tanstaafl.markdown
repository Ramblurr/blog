--- 
layout: post
title: "GSoC Report Week 3: Tanstaafl"
tags: 
- gsoc
- amarok
---
<h4>Project: <a href="http://www.mp3tunes.com">MP3tunes</a> + <a href="http://www.amarok.kde.org">Amarok</a> Integration</h4><span style="font-size:8pt">Total Commits: <a href="http://kollide.net:8060/changelog/~author=link/Amarok" title="All my Amarok commits">51</a> Weekly Commits: 12</span><h4><a name="past">Past 7 Days</a></h4>It was another productive week in #amarok with over 150 commits! In the 12 of those that were mine I managed to do several things.
<ul>
	<li>Added elegant session handling to the MP3tunes service</li>
	<li>Fixed the collection search box, so you can filter your MP3tunes Locker.</li>
	<li>Enabled Copy To Collection functionality, so you can now copy (read: download) mp3tunes tracks to some other collection!</li>
</ul>
Of course, implementing those items wasn't as simple as it sounds, but the features are essential and basic.

The search box (filtering) could use some improvement as currently it only filters via the artist field, but that is a limitation of the MP3tunes API. When I say it 
<em>"only filters via the artist field"</em> I mean that it only matches against artists, so searching for a particular track name will not work. To fully support the filtering feature the MP3tunes API would need to allow you to do something like get a list of artists based on a partial track name in a single request. That is just one example, and yes, I could workaround it by doing multiple queries, however that would slow the entire operation significantly. Users expect the search fields in Amarok to be snappy, not take ~5 seconds per. token they supply. It is certainly not a showstopper, and it functions well enough for now, but hopefully MP3tunes will be open to expanding their API later on down the rode. To be fair I have never come across a web API that supported that sort of complex searching. The <a href="http://ampache.org" title="Ampache!">Ampache</a> service in Amarok suffers from the same lack of functionality.

<em>Interjection: Major props to my GSoC mentor, <a href="http://amarok.kde.org/blog/categories/18-freespirit">Nikolaj</a>, for attempting to explain various parts of Amarok's innards to me, not only once, but the several times it took to get the concepts through my thick skull. Also, he's helped me track down several childish mistakes I've made when I was at my wits end trying to locate them. I can't thank him enough. Hands down he's the best GSoC mentor. </em>

With the addition of "Copy to Collection" Amarok has taken a large step towards being fully integrated with MP3tunes. Up till this week all you could do was browse and stream your MP3tunes Locker. That is fine and dandy, but you could do that from the MP3tunes <a href="http://www.binaryelysium.com/images/mp3tunesPlayer.png">web player</a>, their <a href="http://mp3tunes/com/m">mobile player</a>, <a href="http://www.mp3tunes.com/cb/screenshots/" title="MP3tunes Screenshots">your PS3</a>, or any other number of their <a href="http://www.mp3tunes.com/partner/cb/partnerlist" title="mp3tunes devices">supported devices</a>. However, none of those options allow you to seamlessly download and organize your stored music into your local music collection at the click of a button.  

There is one shortcoming that needs to be addressed at some point before I'm satisfied: there is no progress indicator of any kind when you download tracks. The only way to see if tracks are being downloaded after you press Go is to watch the destination directory for changes. Thankfully this affects all collections you can "copy to/from", not just MP3tunes, so perhaps someone else will feel inclined to whip up a progress indicator. There's no such thing as a free lunch.<h4><a name="upcoming">Upcoming 7 Days:</a></h4>I have one big goal this week:
<ul>
<li>Add MP3tunes Upload features</li>
</ul>
By Monday next week, you will be able to do Copy tracks from your local collection, Ampache collection, and the <a href="http://www.magnatune.com" title="www.magnatune.com">Magnatune</a> database, to your MP3tunes locker.

<img src='http://www.binaryelysium.com/images/amarokCopyToCollection.png' alt='Copy to Collection' class='aligncenter' />

There is quite a bit of work to be done before this can happen, but I will spare you the gritty implementation details until next week after I've committed the code where my mouth is (?).

Of course my weekly predictions wouldn't be complete without a task to fall back on if I happen to complete the aforementioned task in a Ballmer-Fueled rage. After upload is in place there is only one major item left: Syncing. I need to break "Syncing" into manageable actionables (quite a term, eh?) and then lay out some mid-level designs for the process. Later on during the week I will dedicate an entire post to this topic.
