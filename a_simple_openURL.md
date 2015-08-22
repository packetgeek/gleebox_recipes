# The openURL function

Gleebox has a function called openURL.  Its simplest form (used to just open 
a specific web page) is what you'll likely use the most.

Edit glee.js and add an entry in the following format:

    {
    name: 'ttrss',
    method: 'openttrss'
    description: 'Open TT-RSS in a new page',
    statusText: 'opening TT-RSS...'
    },

where:
* name = what you'll type into Gleebox to call the function.  In my case, 
since I use "/" as the trigger, I type "/ttrss" (without the quotes).
* method = the name of the function in the pagecmds.js file.
* description = the short description that shows up in the text box before 
you hit "enter".
* statusText = the short description that shows up in the text box after 
you hit "enter"

Notes:
* Pay attention to which lines terminate with a comma.
* It's believed that "description" and "statusText" are optional.

Edit pagecmds.js and add an entry in the following format:

    Glee.openttrss = function(newtab) {
    Glee.Browser.openURL('http://192.168.2.240/tt-rss', true, true);
    Glee.close();
    };

where:
* openttrss = the name of the function and matches the "method" line that 
you created in glee.js.
* newtab = a custom argument that you can pass to sub functions.  Example: instead of "true" or "false", use "newtab" in the second argument to allow other functions to determine whether or not a new tab should be opened.  Note: "newtab" would need to be used in both this function call and the "openURL" line.  It's messy code but I tend to leave this argument in the function call but don't usually use it.
* http://192.168.2.240/tt-rss = the URL you want opened (edit to suit).
* 1st true = tells Chrome whether or not to open the URL in a new tab.  Valid 
entries are "0", "1", "true", or "false" (without the quotes).
* 2nd true = tells Chrome whether or not focus should be placed on the new tab.  Again, valid entries are "0", "1", "true", or "false" (without the quotes).
* last line = "Glee.empty()" or "Glee.close()" depending on what you want to happen to the text box after pressing "enter" (empty = clear the text, close = close the text box)

Notes:
* Keep in mind that certain function names are reserved for Gleebox use.
* Be sure to research the Gleebox github and other sources when trying to troubleshoot a problem in Gleebox.  More than likely, others have had your issue and have solved it. (Hint: the github URL is: https://github.com/glee/glee/issues/)

