--- 
layout: post
title: The Lessons of a Master
tags: 
- amarok
- campkde
- qt
---
Several of us at Camp KDE—myself included—owe a great debt to <a href="http://www.kdedevelopers.org/blog/432" tilte="Till Adam's blog">Till Adam</a>. When he came to the sunny, beautiful beaches of Jamaica, instead of spending his days lounging on the shore or swimming in the warm Caribbean, he chose to pen himself in a stuffy room with a dozen geeks and teach them Qt.

Till works for Klarälvdalens Datakonsult AB (<a href="http://kdab.net" title="KDAB Website">KDAB</a>), <em>the</em> Qt consultancy firm. Besides working on large-scale, enterprise Qt applications, KDAB provides professional Qt training to such companies as IBM, Boeing, Ericsson, and J.D. Edwards. These training sessions usually run a few thousand Euros <em>per person</em>. With the OK from Nokia and Qt Software, Till provided us with a mini two day training course for free!

While the content and materials Till used during the sessions is copyrighted, the information I learned is not. With his permission I'm going to discuss a few pointers in this post. The topics covered somewhat basic/intermediate Qt skills, so those of you who have been programming with Qt for any length of time might not find anything new or interesting. However, for those, like me, who haven't quite developed our Qt Fu to the Master level, take away tips from here knowing it was passed from a master.

<b>#1 Most Common Performance Issue in Qt</b>
Converting from a QPixmap to QImage too often.

This tip is actually fairly well known, but apparently KDAB consultants run across this mistake very often while in the field. There is a great discussion of this topic over at <a href="http://techbase.kde.org/Development/Tutorials/Graphics/Performance" title="Discussion of QPixmap vs QImage at techbase">KDE's techbase</a>. In summary:
<ul>
<li>A QImage is stored in main memory </li>
<li>A QPixmap is stored in video memory</li>
<li>Converting from a QPixmap to a QImage is a very expensive operation (see the above article for the explanation)</li>
</ul>

<b>#1 Most Common Cause of Crashes in Qt</b>
Deleting this from slots

This tip needs some more explanation. Essentially, a mistake many Qt programmers do is include executable code after emitting a signal.  Consider this flow of execution:

<ul>
<li>The function <em>Produce::blend()</em> emits signal <em>pineapple()</em><li>
<li>The slot <em>slotBlender()</em> deletes the instance of <em>Produce</em></li>
<li>The signal/slot connection returns to the function <em>Produce::blend()</em>, which has some other executable code such as variable assignments after the emit.</li>
<li>Crash. Since the slot deleted <em>Produce</em>, any code following the emit statement that modifies memory is now attempting to write to invalid memory. </li>

One good practice to follow is: don't have any executable code following the last emit statement in your objects' methods.
However, the real solution is: Use <a href="http://doc.trolltech.com/4.4/qobject.html#deleteLater" title="deleteLater() documentation">deleteLater()</a> on your QObjects.

This post is getting somewhat lengthy and I potentially still have two topics to cover (Threading and Model/View). Most likely I'll dedicate a post regarding threading in Qt (I took better notes during that talk) in the next couple days. Many thanks to Till for the sessions, as well as KDAB and Qt Software for allowing them to happen. 
