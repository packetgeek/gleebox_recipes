# Open any URL

Following sets up the "/open" command which allows you to open any URL in a new tab.  Requires one argument (the URL to open).

In glee.js, add the following:

    {
    name: 'open',
    method: 'openit',
    description: 'go to wherever',
    statusText: 'opening page...'
    },

In pagecmds.js, add the following:

    Glee.openit = function() {
    var page = null;
    page = Glee.value().substring(5).replace(' ','');
    var loc = 'http://'+page;
    Glee.Browser.openURL(loc,true,true);
    Glee.close();
    };

