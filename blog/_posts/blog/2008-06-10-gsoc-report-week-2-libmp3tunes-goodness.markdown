--- 
layout: post
title: "GSoC Report Week 2: libmp3tunes goodness"
tags: 
- gsoc
- amarok
---
<h4>Project: <a href="http://www.mp3tunes.com">MP3tunes</a> + <a href="http://www.amarok.kde.org">Amarok</a> Integration</h4><span style="font-size:8pt">Total Commits: <a href="http://kollide.net:8060/changelog/~author=link/Amarok" title="All my Amarok commits">35</a> Weekly Commits: 15</span><h4><a name="past">Past 7 Days</a></h4>This was a busy week. I migrated the existing MP3tunes service in Amarok 2 from making REST calls and parsing XML manually to use libmp3tunes. I created an object oriented encapsulation framework in C++ for libmp3tunes, which is written entirely in c. This means instead of mucking about crafting http queries and worrying about parsing data from XML one can manipulate the Locker in an OO fasion. Here's a little snippet of how libmp3tunes saves work.

Without libmp3tunes if you wanted to fetch a list of artists this is what it would look like:
<pre lang="cpp" line="1">
    QString urlString = "http://ws.mp3tunes.com/api/v1/lockerData?sid=<SESSION_ID>&partner_token=<PARTNER_TOKEN>&output=xml&type=artist";

    urlString = "http://ws.mp3tunes.com/api/v1/lockerSearch?output=xml&sid=<SESSION_ID>&partner_token=<PARTNER_TOKEN>&type=artist&s=" + m_artistFilter;
    
    urlString.replace( "<SESSION_ID>", m_sessionId);
    urlString.replace( "<PARTNER_TOKEN>", CENSORED);

    debug() << "url: " << urlString;

    m_storedTransferJob =  KIO::storedGet(  KUrl( urlString ), KIO::NoReload, KIO::HideProgressInfo );
        connect( m_storedTransferJob, SIGNAL( result( KJob * ) )
            , this, SLOT( artistDownloadComplete( KJob *) ) );

    ArtistList artists;

     //so lets figure out what we got here:
    QDomDocument doc( "reply" );
    doc.setContent( m_storedTransferJob->data() );
    QDomElement root = doc.firstChildElement( "mp3tunes" );
    root = root.firstChildElement( "artistList" );

    QDomNode n = root.firstChild();
    while( !n.isNull() )
    {
        QDomElement e = n.toElement(); // try to convert the node to an element.

        QDomElement element = n.firstChildElement("artistName");
        ServiceArtist * artist = new ServiceArtist( element.text() );

        element = n.firstChildElement("artistId");
        artist->setId( element.text().toInt() );

        ArtistPtr artistPtr( artist );

        artists.push_back( artistPtr );

        m_collection->acquireWriteLock();
        m_collection->addArtist( artistPtr );
        m_collection->releaseLock();

        n = n.nextSibling();
    }
</pre>

With libmp3tunes it looks like this:
<pre lang="cpp" line="1">
    Mp3tunesArtistFetcher * artistFetcher = new Mp3tunesArtistFetcher( m_locker );
    connect( artistFetcher, SIGNAL( artistsFetched( QList<Mp3tunesLockerArtist> ) ), this, SLOT( artistDownloadComplete( QList<Mp3tunesLockerArtist> ) ) );

    ThreadWeaver::Weaver::instance()->enqueue( artistFetcher );

    ArtistList artists;

    foreach(Mp3tunesLockerArtist artist, artistList) {
        ServiceArtist * serviceArtist = new ServiceArtist( artist.artistName() );
        
        serviceArtist->setId( artist.artistId() );

        ArtistPtr artistPtr( serviceArtist );

        artists.push_back( artistPtr );

        m_collection->acquireWriteLock();
        m_collection->addArtist( artistPtr );
        m_collection->releaseLock();

    }
</pre>
Both of those code samples produce this:

<img src='http://binaryelysium.com/images/amarokMp3tunesCollectionBrowser.png' alt='MP3tunes Collection Browser' class='aligncenter' />

Notice that instead of looping through XML and ripping out data, I was able to call getter methods to retrieve the same data. Of course the XML parsing has only been moved to libmp3tunes, but by hiding the MP3tunes API implementation from Amarok it creates more maintainable code.

If none of that made much sense, no worries, the important bit to grasp is that libmp3tunes does these important things:
<ul>
  <li>Encapsulates the MP3tunes API so it is separate from the rest of Amarok.</li>
  <li>Provides an Object Oriented interface to the mp3tunes API. Creating a new session is as easy as  Mp3TunesLocker locker = new Mp3tunesLocker();
  <li>Ensures Amarok is officially supported by mp3tunes as long as they support libmp3tunes.</li>
</ul><h4><a name="upcoming">Upcoming 7 Days:</a></h4>There are a few libmp3tunes shortcomings. One is the lack of a means to detect when a session has expired. Each MP3tunes API request requires a valid session (except of course the initial session-establishing request), and each session times out eventually. When using MP3tunes in Amarok it will be important to elegantly handle session timeouts, for the user does not care about sessions or timeouts. When the user clicks play on an artist they expect it to play, while currently, if the session has timed out Amarok doesn't do anything. This week I will patch libmp3tunes to support detection of timed out sessions. 

Another goal for this week is to fix the search box, so it actually searches.

<img src='http://www.binaryelysium.com/images/amarokMp3tunesSearch.png' alt='MP3tunes Collection Search' class='aligncenter' />

Also, if you right click on an artist in the MP3tunes collection browser you get a "Copy to Collection" option. At the moment it doesn't do anything. After this week is over, hopefully, selecting the "Copy to Collection" option will let you do just that.

<img src='http://www.binaryelysium.com/images/amarokCopyToCollection.png' alt='Copy to Collection' class='aligncenter' /><h4><a name="roadblocks">Foreseeable Roadblocks:</a></h4><a href="http://binaryelysium.com/blog/2008/06/02/gsoc-report-week-1/#roadblocks">Last week's</a> roadblock still stands. In the next few weeks I'll be getting closer to the time when I will need to implement that syncing part of libmp3tunes into Amarok. The licensing issue won't stop me from developing it on my own workstation of course, but it will have to be resolved before I can commit that part of library or code that implements it.
