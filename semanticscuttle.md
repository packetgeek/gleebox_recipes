# sending URL to SemanticScuttle

Following sets up a Gleebox command that will send the URL for the current page to Semantic Scuttle

In glee.js, add the following:

    {
    name: 'ss',
    method: 'scuttle',
    description: 'save a bookmark to SemanticScuttle',
    statusText: 'saving bookmark...'
    },

In pagecmds.js, add the following:

    Glee.scuttle = function() {
    x=document;
    a=encodeURIComponent(x.location.href);
    t=encodeURIComponent(x.title);
    //d=encodeURIComponent(window.getSelection());
    d='';
    open('http://192.168.2.215/ls/www/bookmarks.php/packetgeek?action=add&popup=1&address='+a+'&title='+t+'&description='+d,'SemanticScuttle','modal=1,status=0,scrollbars=1,toolbar=0,resizable=1,width=900,height=600,left='+(screen.width-790)/2+',top='+(screen.height-425)/2);void 0;
        Glee.close();
    };

In the above, you should change "192.168.2.215/ls/www/bookmarks.php" to point at wherever your instance of "bookmarks.php" resides.
