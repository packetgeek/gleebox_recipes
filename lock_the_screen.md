# lock the screen

Following assumes that you're using mate-screensaver.  Modify if you're using somthing else..

In glee.js, add the following entry:

    {
      name: 'lock',
      method: 'lock',
      description: 'activates the screen lock...',
      statusText: 'locking the screen...'
    },

In pagecmds.js, add the following:

    Glee.man = function(newtab) {
      Glee.Browser.openURL("http://127.0.0.1/cgi-bin/lockscreen.cgi",true,false);
      Glee.close();
    };

In /usr/lib/cgi-bin, create a script called lockscreen.cgi and have it contain the following:

    #!/usr/bin/perl
      
    print "Content-type: text/html\n\n";
    print "<html><head>";
    print "<script language='javascript' type='text/javascript'>";
    print "function killself(){";
    print "setTimeout(\"self.close()\",1000);";
    print "}";
    print "</script>";
    print "</head><body onload='killself();self.focus()'>";
        
    system("sudo -Hu tim /bin/bash -c 'export DISPLAY=:0 && \
      /usr/bin/mate-screensaver-command -l'");
        
    print "</body></html>";

Note: above assumes that you have Apache properly installed and configured such that it only listens on 127.0.0.1.
