--- 
layout: post
title: Exporting contacts from Verizon to Gmail
tags: 
- android
- google
- gmail
---
I got a <a href="http://www.t-mobileg1.com/">G1</a> today. 

That deserves a post unto itself, but I wanted to share a solution an annoying issue regarding switching from Verizon to T-Mobile. Before I got the G1 I had a LG-VX9800 (yes, ancient, I know) with around 200 contacts. Obviously one of the first things I wanted to do when I got my G1 was transfer all my contacts from the LG to the G1. There are several ways to do this
<ol>
	<li> Go to a Verizon store and pay $10 for data backup</li>
	<li> Buy a USB Cable for the LG-VX9800, and use <a href="http://www.bitpim.org/">bitpim</a></li>
	<li> Manually copy (type) your contacts into the G1/Gmail</li>
	<li> Use my method</li>
</ol>

There was no way I was going to pay $10 for what should be a simple "Export," so #1 was crossed out. I'm impatient and didn't want to wait for a cable to be delivered and neither did I want to pay the money for one. There goes #2. I didn't even consider #3; I just listed it for completeness sake.

That leaves my somewhat difficult and unreliable method. Basically, what I do is use Verizon's "Backup Assistant" tool to send my contacts to Verizon's website. Then I save the source of the "Print Contacts" page - because there is no export feature. With a little ruby I parse the file into Gmail's <a href="http://theregoesdave.com/2008/10/17/importing-contacts-into-gmail-guide-to-google-contact-csv-fields/">CSV format</a> and import the file via the Gmail contacts page.

Here's a quick howto.

<ul>
	<li> On your Verizon phone go to "Get Going -> Get a New App -> Backup Assistant" and install it for $1.50 a month.</li>
	<li> Follow the prompts and backup your contacts.</li>
	<li> Go to the <a href="http://www.verizonwireless.com/backupassistant">Verizon backup website </a>and sign in.</li>
	<li> View your contacts and click the "Print Contacts" link. Save the source of this page to a file</li>
	<li> <a href="http://www.binaryelysium.com/code/vzwparser.rb">Download this</a> script and run it against the saved html file. Save the output in "contacts.csv"</li>
	<li> Go to the Contacts page in Gmail and select Import, and upload "contacts.csv" <em>Note:</em> I suggest using the "add these imported contacts to" a new group feature. Because you will likely have to merge and cleanup the imported contacts.</li>	
        <li> Import and Enjoy</li>
</ul>

<strong>IMPORTANT:</strong> My script only grabs the following information from the Verizon contact list: Name, Email, Work Phone, Mobile Phone, and Home Phone.
