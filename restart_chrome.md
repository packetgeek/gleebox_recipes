# Restarting Chrome from within Gleebox

Following creates a Gleebox command that allows you to restart Chome.  This is useful when you're doing horrible things to your Gleebox configuration and need to restart Chrome so that your changes are loaded.

In glee.js, add the following:

    {
    name: 'restart',
    method: 'restart',
    description: 'restarts chrome',
    statusText: 'restarting chrome...'
    },

In pagecmds.js, add the following:

    Glee.restart = function() {
    Glee.Browser.openURL('chrome:restart',true,true);
    Glee.close();
    };

The above is simply taking advantage of the restart function built into Chrome.  Please note that Google may remove this function without notice or warning.

This command will restart Chrome and reload the pages that were open when you ran the command.
