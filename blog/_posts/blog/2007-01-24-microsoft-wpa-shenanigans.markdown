--- 
layout: post
title: Microsoft WPA Shenanigans
tags: 
- linux
- windows
---
"If you think technology can solve your security problems, then you don't understand the problems and you don't understand the technology." (Bruce Schneier)

From the Windows XP EULA:
<blockquote>1.1 Installation and use.  You may install, use, access,
display and run <strong>one copy</strong> of the Software on <strong>a single
computer</strong>, such as a <strong><em>workstation</em></strong>, terminal or other
device ("Workstation Computer"). The Software may not
be used by more than two (2) processors at any one
time on any single Workstation Computer. [Emphasis Added]</blockquote>
The Issue: If you have <strong>one</strong> legal installation of windows <strong>on a</strong> partition, and also have Linux, MacOS, or some other OS on another partition you can dualboot just fine. If you install VMware <strong>workstation</strong> on your other OS and configure it with raw disk access to read and boot from your <strong>one</strong> legal installation of windows <strong>on your one computer</strong> WPA detects the different hardware configurations and forces you to re activate. If you use different hardware profiles for virtual native boots.. you are still borked.

The White Elephant: Doesn't this seem like a perfect opportunity for the use of Hardware profiles? Since you only have one installation with different hardware setups this should not break the EULA, or at least the part I quoted above. Since it is impossible to talk to a real life Microsoft <em>technician</em> or lawyer we are at the mercy of their poorly thought out WPA malware.

The Source: If you want to see firsthand the uncanny silence of a MS representative, and simultaneously the inane chatter of MS volunteers (I admit some of them were helpful/sympathetic) check out the <a target="_blank" title="blather from forums.microsoft.com/genuine" href="http://forums.microsoft.com/Genuine/Search/Search.aspx?words=vmware&localechoice=9&SiteID=25&searchscope=forumscope&ForumID=442">posts on the MS forums</a> dealing with this topic.
