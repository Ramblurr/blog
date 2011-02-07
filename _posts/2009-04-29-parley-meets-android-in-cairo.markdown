---
layout: post
title: Parley meets Android in Cairo
tags:
- amarok
- android
- g1
- mobile
- arabic
- egypt
---
I'm exactly three months into my Arabic studies in Cairo, where I've been taking time off university studies and Amarok development. I've realized that acquiring a large vocabulary as fast as you can manage is a crucial part of studying a language intensively, and thanks to the awesome KDE-Edu folks I've been <del>successfully</del> <em>barely</em> keeping up with the hundreds of new words I'm assigned per week with <a href="http://edu.kde.org/parley/" title="Parley's Homepage">Parley</a>.

The major problem I have with Parley is that I have to be in front of my computer to use it!

I know you're laughing. That's like saying a major fault of beer is that you have to <em>drink it</em> to get drunk, after all Parley is a computer program.
You're right, just because I hardly find the time to actually use the computer doesn't mean I should lay the blame on Parley. Technically, I should  blame the denizens of Cairo and their <a href="http://www.flickr.com/photos/tronics/380379732/" title="Typical Cairo Traffic">insane traffic</a>. Seriously, too many of my life's hours are wasted in the smelly, stuffy, taxis of Cairo (today was particularly bad, pardon the rant).

This past weekend I ignored the towering pile of homework and whipped up a little application for Android devices that groks Parley's kvtml2 file format, displays lessons, and provides flashcard exercises. My app is really an Android Port of the J2ME mobile application <a href="http://sourceforge.net/projects/mobvoc/" title="MobVoc project home">MobVoc</a>. Michael, the MobVoc developer, did most of the hard work for me: parsing kvtml2 files into java data structures. Mad props to Michael; I definitely plan to pass along any contribute any bug fixes/optimizations I make to his code (such as sub-lessons support).

The application - unimaginatively dubbed ParleyDroid for now - is extremely bare-bones. Here is the current feature set
<ul>
<li> Pick a kvtml2 file from the SD card </li>
<li> Choose 1 or more lessons to practice </li>
<li> View flashcards of the words in the selected lessons.</li>
<li> Gesture support in the flashcards: Long Press marks card as known, Fling Left/Right changes to Next/Prev card.
<li> Each practice session has a short-term memory: i.e., if you mark a card as known you won't see it again that session but if you restart the session you will.</li>
<li> <em>Arabic Support</em> - if the 2nd language is Arabic, it will be rendered correctly on screen</li>
</ul>

The last feature is probably the most noteworthy. Android, by default does not support RTL or non-Latin scripts, but with a little Android-trickery-that-deserves-another-blog-post I'm finally able to practice my vocabulary in the back of the taxi or while walking along the Nile.

Binary and Source:
<a href="http://www.binaryelysium.com/code/ParleyDroid-0.1.tar.gz" title="ParleyDroid Source">ParleyDroid Source</a> and
<a href="http://www.binaryelysium.com/code/ParleyDroid-0.1.apk" title="ParleyDroid Android Binary">ParleyDroid Android Binary</a>

Obligatory Screenshots (click for full view):

<a href="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_pick_file.png"><img src="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_pick_file-150x150.png" alt="ParleyDroid Pick File Screen" title="ParleyDroid Pick File Screen" width="150" height="150" class="alignnone size-thumbnail wp-image-123" /></a><a href="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_lessons.png"><img src="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_lessons-150x150.png" alt="ParleyDroid Lessons Screen" title="ParleyDroid Lessons Screen" width="150" height="150" class="alignnone size-thumbnail wp-image-121" /></a>
<a href="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_word1.png"><img src="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_word1-150x150.png" alt="ParleyDroid First Word Screen" title="ParleyDroid First Word Screen" width="150" height="150" class="alignnone size-thumbnail wp-image-124" /></a><a href="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_word2_menu.png"><img src="http://www.binaryelysium.com/blog/wp-content/uploads/2009/04/pd_word2_menu-150x150.png" alt="ParleyDroid Second Word Screen w/ Arabic" title="ParleyDroid Second Word Screen w/ Arabic" width="150" height="150" class="alignnone size-thumbnail wp-image-125" /></a>
