# send current page to PrintFriendly

Following sneds the current page to the PrintFriendly service.

In glee.js, add the following entry:

  {
    name: 'print',
    method: 'print',
    description: 'convert page to PDF or print',
    statusText: 'converting...'
  },

In pagecmds.js, add the following:

  Glee.print = function() {
    var src, url;
    src=encodeURIComponent(document.location.href);
    url="https://www.printfriendly.com/print/?source=homepage&url="+src;
    Glee.Browser.openURL(url,true,true);
    Glee.close();
  };

