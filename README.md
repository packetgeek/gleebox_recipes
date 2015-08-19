# gleebox_recipes
A collection of recipes and mods that I've inflicted on gleebox.  Keep in mind that I'm using gleebox in a manner not intended by its authors.  Unless otherwise noted, these are commands that are added to gleebox by editing the glee.js and pagecmds.js files.

When using the Glee.OpenURL function, it expects three arguments.
* Arg 1 = whichever URL you want to call, doesn't have to be http: or https:
* Arg 2 = open a new tab? (0 or false = no, 1 or true = yes, "newtab" = dependent on input (enter = 0, shift-enter = 1))
* Arg3 = selected? - if a new tab is opened, should focus be placed on it?  (1/true or 0/false)
