# navigate up one level in URL

Following causes the browser to navigate to the next higher level in the URL.  

In glee.js, add the following entry:

  {
    name: 'top',
    method: 'top',
    description: 'navigate up one level',
    statusText: 'opening page...'
  },

In pagecmds.js, add the following:

  Glee.up = function() {
    window.location=document.location.href.replace(/\/$/,'').split('/').slice(0,-1).join('/')+"/";
  }


