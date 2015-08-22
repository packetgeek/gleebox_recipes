# Reload the current page

Following causes Chrome to reload the currently focused page.

In glee.js, add the following:

    {
    name: 'reload',
    method: 'reload',
    description: 'reloads current page',
    statusText: 'reloading page...'
    },

In pagecmds.js, add the following:

    Glee.reload = function() {
    document.location.reload(true);
    Glee.close();
    };

Don't forget to restart Chrome before attempting to use this command.
