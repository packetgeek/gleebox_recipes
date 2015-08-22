# Opening more than one URL

You can use a single Gleebox command to open more than one tab at a time.  Syntax for doing so is simple, just add another line to the called function.  Example follows.

In glee.js, add something like the following (a normal entry):

    {
    name: 'argleblarg',
    method: 'openmany',
    description: 'open multiple pages',
    statusText: 'opening pages...'
    },


In pagecmds.js, add something like the following:

    Glee.openmany = function() {
    Glee.Browser.openURL('http://www.redhat.com', true, false);
    Glee.Browser.openURL('http://slashdot.org', true, true);
    Glee.Browser.openURL('https://www.google.com', true, false);
    Glee.close();
    };

Note that only one of the openURL lines should have the third argument (i.e., focus) set to true.  The others should be set to false.
