These commands are implemented in the glee.js and pagecmds.js files, AFTER you've installed the gleebox extension for the Chrome browser.  To figure out the files location, run the following from your home directory:

    find .config/ -name glee.js

When editing the glee.js file, the new commands should be entered somewhere after the "commands: [" line.  When editing the pagecmds.js file, the new entry can be made anywhere in the file (just not inside another command, obviously).

Note: in recent versions, Chrome periodically checks extensions for changes and disables anything that's been modified (e.g., gleebox).  To get around this, you'll need to down load the source code for gleebox (http://github.com/glee/glee), make your modifications to that, enable Chrome's developer feature (on the Extensions page), and load gleebox locally.

See also: http://www.neighborhoodtechie.com/2015/05/adding-page-commands-to-gleebox.html
