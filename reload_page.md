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

Above is pretty basic but sometimes useful.  It also hints at how other Javascript commands can be used in Gleebox.
