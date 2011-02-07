--- 
layout: post
title: GSoC Report - Week 1
tags: 
- gsoc
- amarok
---
<h4>Project: <a href="http://www.mp3tunes.com">MP3tunes</a> + <a href="http://www.amarok.kde.org">Amarok</a> Integration</h4>

<em style="font-size: 8pt">Prescriptum: These weekly reports will likely contain a bit of technical information that only other Amarok developers will understand. I do not like that idea, as I want these reports to be grokable by all, but since I haven't yet decided on a format to present the info in a manner I like this will have to do for this first week. </em>

<h4>Past 7 Days:</h4>
I started coding for <a href="http://code.google.com/soc/2008/" title="GSoC">GSoC</a> last Tuesday (May 27th) beginning with a simplification of the ServiceCollection hierarchy by combining ServiceDynamicCollection and ServiceCollection into one class. I also started creating the ServiceCollectionLocation's. It is not implemented anywhere yet, and won't need to be for awhile, but I started it as at the time I was waiting on mp3tunes to deliver their c sdk. 

Leeo kindly created mp3tunes icons, which I committed on Saturday. 
<img src="http://www.binaryelysium.com/images/emblem-mp3tunes-amarok16.png" alt="mp3tunes icon" /> and <img src="http://www.binaryelysium.com/images/mp3tunes-amarok-48.png" alt="Mp3tune icon" />

During the week I kept nudging the mp3tunes developers to send me the c sdk, and Saturday the nudging paid off as I received a pre-release version of libmp3tunes. Even though it is a pre-release it is complete enough to match the current mp3tunes feature set in Amarok2. On Sunday I added libmp3tunes to the src tree, including the dependency detection. libmp3tunes is dependent on curl and libxml2, and if someone does not have them mp3tunes will be excluded from the build thanks to cmake. 

Finally, today, I committed a ~750 line c++ wrapper for libmp3tunes to compartmentalize the unsightly c code.

You can see all my commits here: 
<a href="http://kollide.net:8060/changelog/~author=link/Amarok">http://kollide.net:8060/changelog/~author=link/Amarok</a>

<h4>Upcoming 7 Days:</h4>
There are still a few functions left TODO in the c++ wrapper for libmp3tunes, so I'll complete those this week. Then I plan to start migrating the existing service to use the library functions. I expect this will take all week, so my goal for the next report is to have the migration complete and a working Mp3tunes service utilizing the library. If my time estimation ends up being too long, and I finish the migration early, I'll work on the Mp3tunesCollectionLocation functionality so you can copy tracks from Mp3tunes to the local collection in a manner similar to the Magantune service.

<a name="roadblocks"><h4>Forseeable Roadblocks:</h4></a>
The syncing part of libmp3tunes is not licensed and not complete. However, the MP3tunes developers have been particularly responsive the past several weeks, so I am optimistic they will pull through.

<h4>Reflections:</h4>
I am amazed at how much I learned this week. To keep this brief here is a list of some things I've learned:
<ul>
 	<li>How to do basic cmake things like define optional deps and exclude portions of an app if they aren't met.</li>

 	<li>Before this week I had never even seen object oriented c before.</li>

	<li>Also I learned how to combine c and c++ code in the same program (extern!).</li>

	<li>KDE4 is a beast and breaking it is bad news.</li>

</ul>
