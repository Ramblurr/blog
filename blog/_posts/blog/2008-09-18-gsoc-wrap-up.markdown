--- 
layout: post
title: GSoC Wrap Up
tags: 
- gsoc
- amarok
- mp3tunes
---
If there was a blogger award for "Most likely to make timely posts", then in no possible world would I even be considered for the award. I could list some <acronym title="School">excuses</acronym> <acronym title="Travel">that</acronym> <acronym title="Life">sound</acronym> <acronym title="Moving In">legit</acronym> in my head, but the real reason I don't feel motivated to post often (or on time) is because I'd rather spend that time in Google Reader reading everyone else's exciting content (that was not sarcastic).

So, lets see... last time I posted I was en route to Akademy 2008 (the KDE developers conference). That was July 30th, now, a month and a half later I am back from Europe (which was amazing), GSoC is over (sad), and class has started (jury's still out).

<strong>Current Status of the MP3tunes Amarok Service</strong>

The Good (Works)
<ul>
<li>Browsing & Streaming</li>
<li>Querymaker is as functional as possible with the current API</li>
<li>Manual Downloading from MP3tunes to Local Collection</li>
<li>Manual Uploading from any Collection to MP3tunes</li>
</ul>
The Bad (Doesn't work)
<ul>
<li>AutoSync - 80%- <em>The code is there, however there are problems with the daemon not receiving signals from the MP3tunes' servers</em></li>
<li>MP3tunes playlists support - 0%- <em>Never got started on this</em></li>
</ul>

The Ugly

There is one large issue I am still wrestling with. The details of the issue are complicated, but essentially it deals with the way Amarok handles remote tracks in playlists across sessions. Generally, remote tracks' metadata isn't cached by Amarok for use between multiple sessions. So, if you add an mp3tunes track to a playlist in Amarok, then restart Amarok and try to play that playlist the mp3tunes track is blank. Now, there exists a method for retrieving that metadata, however it was originally implemented synchronously. When you are retrieving metadata for any significant number of tracks (10+) synchronously, and each one of those retreivals is an HTTP Get request you end up blocking the GUI thread. At Akademy I hacked a way to do this asynchronously, but it is a really nasty hack. I've got code on my computer that implements this feature correctly, but it has the nasty habit of crashing Amarok every so often.

Between classes, marching band, homework, and other responsibilities I'm working on getting this ironed out and committed. Hopefully this will happen before the 2.0 release, because right now using MP3tunes in Amarok across sessions is slow and annoying.
