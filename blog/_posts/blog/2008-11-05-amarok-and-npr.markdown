--- 
layout: post
title: "Amarok & NPR :: 13 Years of News Media Now Available at Your Fingertips"
tags: 
- amarok
- npr
---
Earlier this summer I had noticed that National Public Radio (<a href="http://www.npr.org" title="NPR.org">NPR</a>) launched a brand new <a href="http://www.npr.org/blogs/inside/2008/07/npr_api_is_live_on_nprorg.html" title="NPR API Announcement">open API</a> based on open source technologies. My initial reaction was at best skeptical. I assumed any sort of "API" released by a major media outlet would turn out to be nothing more than a few customizable RSS feeds. If the company was particularly progressive the RSS feeds might include full articles, rather than the neutered one-sentence teasers you find in <a href="http://www.nytimes.com/services/xml/rss/nyt/HomePage.xml" title="NYT's neutered feed">all</a> <a href="http://www.foxnews.com/xmlfeed/rss/0,4313,0,00.rss" title="Fox News' neutered feed">the</a> <a href="http://feeds.cbsnews.com/CBSNewsMain" title="CBS' neutered feed">big</a> <a href="http://rss.cnn.com/rss/cnn_topstories.rss" title="CNN's neutered feed">name's</a> syndicated content.

I couldn't have been more mistaken. NPR's API is no small potatoes. Just take a look at the comprehensive <a href="http://www.npr.org/api/queryGenerator.php" title="NPR API Query Generator">Query Generator</a> to get an inkling of the types of complex queries you can create. Looking at the Query Generator also sheds some light on the content you can retrieve using the API. The <a href="http://www.npr.org/api/index.php" title="NPR API Overview">API's main page</a> says the API exposes the <em>entire</em> NPR archive of content starting from the launch of the NPR website in 1995. Just how big is this archive? Over 250,000 stories including text, images, video, and audio! 

This quote from the article announcing the API caught my eye immediately:
<blockquote>
There were quite a few questions that we addressed when developing the API, but one thing that was not really in question was the need to open as much of our content as possible. (( <a href="http://www.npr.org/blogs/inside/2008/07/npr_api_is_live_on_nprorg.html" title="NPR API is Live on NPR.org">NPR API is Live on NPR.org</a>))
</blockquote>

This isn't the first open media API. BBC was the first to offer a public open access API, however BBC's API is restricted to the content from the past 7-days. Seven days! That's nothing compared to the (approx.) 4748 days - and counting - that NPR's API offers. NPR and the BBC are two large companies leading the technological shift towards open and free information.

But that's only half the story. 

After discovering this fantastic API I had to do something with it, and the new service architecture in <a href="http://www.amarok.kde.org">Amarok 2</a> provided the perfect platform to build a NPR mashup. That was several months ago, and at the time the scripting API in Amarok was still being flesh out (Thanks to <a href="http://amarok.kde.org/en/aggregator/sources/16" title="Peter's Amarok syndicated blog">Peter</a>). On Monday I noticed the BBC scriptable service <a href="http://amarok.kde.org/blog/archives/826-There-is-a-BBC-in-my-Amarok.html" title="There is a BBC in my Amarok">Nikolaj had created</a> for Amarok 2. I happened to have several hours of free time, so I cooked up a similar service for NPR:

<a href="http://www.binaryelysium.com/images/Amarok_npr2.png"><img width='400' height='239' style="border: 0px;" src="http://www.binaryelysium.com/images/Amarok_npr2_thumb.png" /><a/><a href="http://www.binaryelysium.com/images/Amarok_npr3.png"><img width='400' height='239' style="border: 0px;" src="http://www.binaryelysium.com/images/Amarok_npr3_thumb.png" /></a><a href="http://www.binaryelysium.com/images/Amarok_npr1.png"<img width='400' height='239' style="border: 0px;" src="http://www.binaryelysium.com/images/Amarok_npr1_thumb.png" /></a>

You can get it at <a href="http://www.kde-apps.org/content/show.php?content=92543" title="kde-apps NPR Service">kde-apps</a> or via the "Get More Scripts" button in Amarok 2's Script Manager.

There is definitely room for improvement and in fact here are a few things I plan to do with it:
<ul>
<li>Display more than 20 stories under a category</li>
<li>Sort content by date</li>
<li>Support searching</li>
<li>Display the full articles, with images, in the context view</li>
</ul>

Major props and thanks go out to the entire NPR technical team and all the contributors who made API a reality.
