# Show a man page

Following converts the current page to an epub, using dotepub (https://dotepub.com/).  Following is basically a re-use of the code tied to their browser button.

In glee.js, add the following entry:

    {
    name: 'epub',
    method: 'epub',
    description: 'convert current page to epub',
    statusText: 'converting...'
    },

In pagecmds.js, add the following:

    Glee.epub = function() {
    try{
      var d=document,w=window;
      if(!d.body||d.body.innerHTML=='')throw(0);
      var s=d.createElement('link'),h=d.getElementsByTagName('head')[0],i=d.createElement('div'),j=d.createElement('script');
      s.rel='stylesheet';
      s.href='//dotepub.com/s/dotEPUB-favlet.css';
      s.type='text/css';
      s.media='screen';
      h.appendChild(s);
      i.setAttribute('id','dotepub');
      i.innerHTML='<div id="status"><p>Conversion in progress...</p></div>';
      d.body.appendChild(i);
      j.type='text/javascript';
      j.charset='utf-8';
      j.src='//dotepub.com/j/dotepub.js?v=1.2&s=1&t=epub&g=en';
      h.appendChild(j);
    }
    catch(e){
      w.alert('The page has no content or it is not fully loaded. Please, wait till the page is loaded.');
    }
    Glee.close();
    };

Note: I don't use this one 'cause the utility doesn't recognize carriage returns (i.e., for some pages, the output tends to be mashed together). I prefer the output from Wallabag.

