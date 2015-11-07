# open a shell

Following is another of the "dangerous" recipes.  Take care if you implement this recipe.  It is assumed that you are able to properly configure sudo (via visudo) and that you have Apache listening only on the "lo" interface.

In glee.js, add the following entry:

    {
        name: 'shell',
        method: 'shell',
        description: 'open a shell',
        statusText: 'sending command...'
    },

In pagecmds.js, add the following:

    Glee.shell = function() {
        Glee.Browser.openURL('http://127.0.0.1/cgi-bin/shell.cgi',true,false);
        Glee.close();
    };

Save the following as shell.cgi in /usr/lib/cgi-bin.  Be sure to edit YOURUSER.

    #!/usr/bin/perl
          
    print "Content-type: text/html\n\n";
    print "<html><head>";
    print "<script language='javascript' type='text/javascript'>";
    print "function killself(){";
    print "setTimeout(\"self.close()\",1000);";
    print "}";
    print "</script>";
    print "</head><body onload='killself();self.focus()'>";
          
    system "sudo -Hu YOURUSER /bin/bash -c 'export DISPLAY=:0 && /usr/bin/gnome-terminal -e bash --working-directory=$HOME & ' >/dev/null";
          
    print "</body></html>";
