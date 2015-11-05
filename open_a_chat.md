# open a private chat in XChat

Following is another of the "dangerous" recipes.  Take care if you implement this recipe.  It is assumed that you are able to properly configure sudo (via visudo) and that you have Apache listening only on the "lo" interface.

Following assumes that Apache2 and wmctrl are installed, and dbus is active.

Gleebox command syntax (to start chatting with joat) would be:  /chat joat

In glee.js, add the following entry:

  {
    name: 'chat',
    method: 'chat',
    description: 'open a chat with a specific user',
    statusText: 'opening chat...'
  },

In pagecmds.js, add the following:

  Glee.chat = function() {
    var user = null;
    user = Glee.value().substring(5).replace(' ','');
    Glee.Browser.openURL('http://127.0.0.1/cgi-bin/xchat.cgi?action=chat&name='+user,true,false);
    Glee.close();
  };

Save the following as xchat.cgi in /usr/lib/cgi-bin.  Be sure to edit YOURUSER.

  #!/usr/bin/perl
  
  use CGI;
  
  my $query=new CGI;
  
  my $action = $query->param("action");
  chomp $action;
  my $name = $query->param("name");
  chomp $name;
  
  print "Content-type: text/html\n\n";
  print "<html><head>";
  print "<script language='javascript' type='text/javascript'>";
  print "function killself(){setTimeout('self.close()',1000);};";
  print "</script>";
  print "</head><body onload='killself();self.focus()'>";
  
  # following unhides, then raises xchat, then opens query
  system("sudo -u YOURUSER /bin/bash -c \"export DISPLAY=:0 && dbus-send --dest=org.xchat.service --type=method_call /org/xchat/Remote org.xchat.plugin.Command string:'gui show'\"");
  system("sudo -u YOURUSER /bin/bash -c \"export DISPLAY=:0 && wmctrl -a xchat\"");
  system("sudo -u YOURUSER /bin/bash -c \"export DISPLAY=:0 && dbus-send --dest=org.xchat.service --type=method_call /org/xchat/Remote org.xchat.plugin.Command string:'query $name'\"");
  
  print "</body></html>";
  
