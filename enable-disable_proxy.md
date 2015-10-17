# Enable and disable the browser proxy

Note: this is one of those actions which falls into the "dangerous" category.

Following assumes that you know how to configure sudo using visudo and have Apache configured on your workstation such that it only listens on the "lo" interface. This is useful when working with the Burp Suite.  This is known to work on various flavors of Kali and Ubuntu.

In glee.js, add the following entry:

  {
    name: 'proxy',
    method: 'proxy',
    description: 'turns the proxy on or off',
    statusText: 'sending command...'
  },

In pagecmds.js, add the following:

  Glee.proxy = function() {
    var setting = null;
    var loc = null;
    setting = Glee.value().substring(6).replace(' ','');
    if(setting==="on") {
      loc="http://127.0.0.1/cgi-bin/proxy.cgi?action=add";
    }
    if(setting==="off") {
      loc="http://127.0.0.1/cgi-bin/proxy.cgi?action=off";
    }
    Glee.Browser.openURL(loc,true,false);
    Glee.close();
  };

Save the following as proxy.cgi in /usr/lib/cgi-bin.  Besure to edit YOURUSER and the IP addresses involved.


#!/usr/bin/perl

use CGI;

my $query=new CGI;

my $action = $query->param("action");
chomp $action;

print "Content-type: text/html\n\n";
print "<html><head>";
print "<script language='javascript' type='text/javascript'>";
print "function killself(){";
print "setTimeout(\"self.close()\",1000);";
print "}";
print "</script>";
print "</head><body onload='killself();self.focus()'>";

if($action eq "add") {
	system("sudo -u YOURUSER dbus-launch /usr/bin/gsettings set org.gnome.system.proxy.http host '127.0.0.1'");
	system("sudo -u YOURUSER dbus-launch /usr/bin/gsettings set org.gnome.system.proxy.http port 8080");
	system("sudo -u YOURUSER dbus-launch /usr/bin/gsettings set org.gnome.system.proxy ignore-hosts \"['localhost', '127.0.0.0/8', '192.168.2.0/24']\"");
	system("sudo -u YOURUSER dbus-launch /usr/bin/gsettings set org.gnome.system.proxy mode 'manual'");
	print "<br>";
	print "proxy on\n";
}

if($action eq "off") {
	system("sudo -u YOURUSER dbus-launch /usr/bin/gsettings set org.gnome.system.proxy mode 'none'");
	print "proxy off\n";
}

print "</body></html>";
