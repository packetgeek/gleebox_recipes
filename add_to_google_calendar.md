# add to Google Calendar

Following asks for an event name and opens the dialog for creating a Google Calendar event.

In glee.js, add the following entry:

    {
      name: 'cal',
      method: 'cal',
      description: 'add to Google calendar',
      statusText: 'opening calendar...'
    },

In pagecmds.js, add the following:

    Glee.cal = function() {
      var s;
      if(window.getSelection){
        s=window.getSelection();
      }else{
        s=document.selection.createRange().text;
      };
      var t=prompt('Please enter a description for the event',s);
      if(t){
        void(window.open(encodeURI('http://www.google.com/calendar/event?ctext='+t+'&action=TEMPLATE&pprop=HowCreated%3AQUICKADD'),'gcal'));
      }else{
        void(s);
      }; 
    };
  
  
This was adapted from Merlin Mann's Quix entry at:
  
  https://github.com/merlinmann/quix-mann/blob/master/mann-quix%20copy.txt
