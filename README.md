# gleebox_recipes
This is a collection of recipes and mods that I've inflicted on gleebox.  Keep in mind that I'm using gleebox in a manner not intended by its authors.  Unless otherwise noted, these are page commands that are added to gleebox by editing the glee.js and pagecmds.js files.  I've written these so that I can avoid having to use Yubnub and Quix, allowing me to run various commands without having connectivity to the Internet (e.g., I can still control the office lights).

Please note that some of these are not my work.  Some are from unknown sources (some from the original browser extension).  I will attempt to give credit where possible.

Also please note that these examples are intended to be manually added to your current Gleebox instance.  You cannot download them and drop them in any folder.  You can't get there from here (at least not that way).

## Concerning the Glee.Browser.openURL function
When using the Glee.Browser.openURL function, it expects three arguments.
* Arg 1 = whichever URL you want to call, doesn't have to be http: or https:
* Arg 2 = open a new tab? (0 or false = no, 1 or true = yes, "newtab" = dependent on input (enter = 0, shift-enter = 1))
* Arg3 = selected? - if a new tab is opened, should focus be placed on it?  (1/true or 0/false)

There actually use cases where arg2 would be true and arg3 would be false.  Example: adding an URL to Wallabag so that you can read it later.  You don't neeed to see the window open and then immediately close.

## Other
Various other horrible things I've done to gleebox and my machine
* I switched from the "g" trigger to "/".  Doing so allows me to use gleebox within Google sites.
* I've added foot pedals to my machine.  I'm getting older and aren't as flexible as I used to be.  Having to bend my fingers around to press the Ctrl, Fn, Win, Alt, or Menu keys requires that I move a hand and look down at the keys (almost as distracting as reaching for the mouse).
