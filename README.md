PhantomCurl(Python3)
===========

Python wrapper around [PhantomJS][phantomjs] headless browser for advanced web scraping.
Apart of the page content, it can record all requests and responses from the
web page, or collect content of all the IFrames.

If used as a command line tool, it returns data in JSON format.


Installation
===========

PhantomCurl is a wrapper around [PhantomJS][phantomjs], so first you should install PhantomJS [from the project's page][phantomjs-install]

[phantomjs]:http://phantomjs.org/
[phantomjs-install]:http://phantomjs.org/download.html

PhantomJS should be visible system wise:

    which phantomjs

If the binary is not visible system-wide, you should set the environment variable PHANTOMJS_BIN to point to the PhantomJS binary.

Now, build and install the python egg:

    make && make install


Command line tool
================

You can use the script as a command line tool with:

    python -mphantomcurl --help

Returns data in JSON format


Returned values
===============

`fetch()` returns dictionary with the following fields:

    url             - URL fed to the fetch function
    requests        - all requests captured
    responses       - all responses captured
    content         - content of the web page
    timestamps      - [start, end], seconds
    version         - version of the JS script
    command_line    - command line arguments passed to the JS 
    frames          - IFrames found on the page. `frames` can contain other frames recursively


IFrames inspection
==================

The script allows deep iframes inspection (-f option). For each iframe it reports `src`, `id` and its content. Then for each frame it check if it contains more iframes and reports them, recursively.

