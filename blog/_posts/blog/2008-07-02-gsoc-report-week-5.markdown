--- 
layout: post
title: "GSoC Report Week 5: Harmonizing Amarok"
tags: 
- gsoc
- amarok
- mp3tunes
---
<h4>Project: <a href="http://www.mp3tunes.com">MP3tunes</a> + <a href="http://www.amarok.kde.org">Amarok</a> Integration</h4><span style="font-size:8pt">Total Commits: <a href="http://kollide.net:8060/changelog/~author=link/Amarok" title="All my Amarok commits">106</a> Weekly Commits: 26</span><h4><a name="past">Past 7 Days</a></h4>I usually aim to post these reports on Monday, but I'm usually wrapping up a final commit or two on Monday night so I wait till Tuesday to post the report. Well now it's 3:30 on Wednesday morning and I'm just starting. My last commit for "this week" was, oh, about 30 seconds ago.

During the last 7 days I:
<ul>	<li>Patched libmp3tunes to support track fetching based off a filekey.</li>	<li>Used the aforementioned patch in Amarok to enable saving of MP3tunes tracks to playlists.</li>	<li>Made the MP3tunes Service "Lazy Load" upon Amarok's start-up.</li>	<li>Fixed misc non-mp3tunes related Amarok bugs.</li>	<li>Added libmp3tunes::Harmony to the source tree.</li>	<li>Created a harmony daemon that runs asynchronously within Amarok.</li></ul>

As usual you can see a list of my most recent commits via my <a href="http://kollide.net:8060/changelog/~author=link/Amarok">fisheye</a> page.

<strong>What the heck is this Harmony nonsense?</strong>

Harmony, itself, is a subset of libmp3tunes that provides an api for receiving event notifications from the MP3tunes servers. Essentially, what it boils down to is harmony enables the MP3tunes servers to notify Amarok when a user's Locker has been changed. This will allow Amarok to assess the changes and perform an appropriate action (e.g., download a new track). 

Suppose Jenni buys a song from <a href="http://www.eclassical.com/">eClassical</a> and has it loaded directly to her locker. When this happens her Amarok will receive a notification: <em>"Hey Amarok, Jenni just had a track added to her locker."</em> At which point Amarok will seamlessly download the track to Jenni's local collection.<h4><a name="upcoming">Upcoming 7 Days</a></h4>Pretty cool right? Sure is, there's just one caveat: it's not working yet. Getting harmony to play nice with Amarok was a challenge that took a couple days, but as of this morning harmony is running in Amarok.

By this time next week I plan to have harmony fully integrated with Amarok, so the above scenario can actually take place. Even though the feature freeze that was announced for Amarok 2.0 technically doesn't include me, I will still be taking some time to polish all the work I've done since May.
