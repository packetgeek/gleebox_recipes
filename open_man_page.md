# Show a man page

Following assumes that you have man2html installed somewhere.

In glee.js, add the following entry:

    {
    name: 'man',
    method: 'man',
    description: 'find the man page for...',
    statusText: 'opening man page for...'
    },

In pagecmds.js, add the following:

    Glee.man = function(newtab) {
    var page = null;
    page = Glee.value().substring(4).replace(' ','');
    var loc = 'http://192.168.2.215/cgi-bin/man/man2html?query='+page;
    Glee.Browser.openURL(loc,true,true);
    Glee.close();
    };

Edit the above and change the "var loc" line so that it points at your instance of man2html.  On most Linux systems, man2html is an installable package.  If it isn't, more info is available at: http://www.w3.org/Tools/man2html.html

Note: you may want to copy favorite man pages from other systems onto wherever you're running man2html.
