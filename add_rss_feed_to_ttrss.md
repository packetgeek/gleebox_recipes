# Replace Google Reader with TT-RSS

Gleebox still contains a default function which adds the RSS feed for the current page to Google Reader.  Problem is that Google Reader no longer exists.  The good news is that you can use an instance (yours or someone else's) of TT-RSS instead of Google Reader.

In glee.js, add the following:

    {
    name: 'rss',
    method: 'getRSSLink',
    description: 'Open the RSS feed of this page in TT-RSS',
    statusText: 'Opening feed in TT-RSS...'
    },

In pagecmds.js, add the following:

    Glee.getRSSLink = function() {
    Glee.Browser.openURL('http://192.168.2.240/tt-rss/public.php?op=subscribe&feed_url='+encodeURIComponent(location.href),true,true);
    Glee.close();
    };

where:
* "192.168.2.240" is the IP address of the server hosting the TT-RSS instance.
