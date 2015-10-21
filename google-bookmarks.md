# sending URL to Google Bookmarks

Following sets up a Gleebox command that will send the URL for the current page to Google Bookmarks.

In glee.js, add the following:

  {
    name: 'gbm',
    method: 'gbm',
    description: 'add to Google Bookmarks',
    statusText: 'sending URL...'
  },

In pagecmds.js, add the following:

  Glee.gbm = function() {
    var a=window,b=document,c=encodeURIComponent,d=a.open("https://www.google.com/bookmarks/mark?op=edit&output=popup&bkmk="+c(b.location)+"&title="+c(b.title),"bkmk_popup","left="+((a.screenX||a.screenLeft)+10)+",top="+((a.screenY||a.screenTop)+10)+",height=700px,width=900px,resizable=1,alwaysRaised=1");
    a.setTimeout(function(){d.focus()},300);
    Glee.close();
  };

Above should open a pop-up window which allows you to enter information about the link before saving it.
