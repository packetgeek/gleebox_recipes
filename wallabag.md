#Wallabag

I use three Gleebox commands when working with Wallabag:

* /bag - saves the current page to Wallabag
* /walla - opens the Wallabag landing page
* /wb - opens my weekly script for generating "What have I read?" type messages

## /bag

Add the following to glee.js:

    {
    name: 'bag',
    method: 'bagit',
    description: 'grab web page to read later',
    statusText: 'grabbing page...'
    },

Add the following to pagecmds.js:

    Glee.bagit = function(newtab) {
    if(top['bookmarklet-url@wallabag.org']){top['bookmarklet-url@wallabag.org'];}else{(function(){var url = location.href || url;window.open('http://192.168.2.215/wallabag/?action=add&autoclose=true&url=' + btoa(url),'_blank');})();void(0);}
    Glee.close();
    };

Above is basically lifted from the Javascript attached to the marklet button that the Wallabag authors have provided, with a slight modification so that it points to my instance of Wallabag.

## /walla

Add the following to glee.js:

    {
    name: 'walla',
    method: 'walla',
    description: 'opens the local page for Wallabag',
    statusText: 'opening page...'
    },

Add the following to pagecmds.js:

    Glee.walla = function(newtab) {
    Glee.Browser.openURL('http://192.168.2.215/wallabag',true,true);
    Glee.close();
    };

# /wb

This basically is a simple openURL command which points to my script that will generate the "What's been in my bag this week?" blog post.  See https://github.com/packetgeek/wbimb for more detail.

Add the following to glee.js:

    {
    name: 'wb',
    method: 'wb',
    description: 'Whats been in my bag?',
    statusText: 'Loading page...'
    },

Add the following to pagecmds.js:

    Glee.wb = function(newtab) {
    Glee.Browser.openURL('http://192.168.2.215/wbimb/', true, true);
    Glee.close();
    };

As always, once you modify the files, you'll need to restart the browser so that the changes are loaded.

