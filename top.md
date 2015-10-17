# navigate to top level in URL

Following causes the browser to navigate to the top level in the URL.  

In glee.js, add the following entry:

  {
    name: 'top',
    method: 'top',
    description: 'navigate up one level',
    statusText: 'opening page...'
  },

In pagecmds.js, add the following:

  Glee.top = function() {
    window.location=document.location.protocol+"//"+document.location.host;
  }

