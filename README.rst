.. _docs.testmunk.com: http://docs.testmunk.com
.. _bower: http://www.bower.io
.. _sphinx: http://www.sphinx-doc.org
.. _compass: http://www.compass-style.org
.. _sass: http://www.sass-lang.com
.. _wyrm: http://www.github.com/snide/wyrm/
.. _grunt: http://www.gruntjs.com
.. _node: http://www.nodejs.com
.. _hidden: http://sphinx-doc.org/markup/toctree.html
.. _sphinx_rtd_theme: https://github.com/snide/sphinx_rtd_theme
.. _docs: https://github.com/testmunk/docs

*********************
Testmunk Sphinx Theme
*********************

View a working demo over on docs.testmunk.com_.

This is a prototype mobile-friendly sphinx_ theme made for docs.testmunk.com_. It's
a fork from the official ReadTheDocs sphinx_ theme at the sphinx_rtd_theme_ repository.

**This repo also exists as a submodule within the docs_ repo itself**, so please make your edits to
the SASS files here, rather than the .css files on the docs_ repository.

How the Table of Contents builds
================================

Currently the left menu will build based upon any ``toctree(s)`` defined in your index.rst file.
It outputs 2 levels of depth, which should give your visitors a high level of access to your
docs. If no toctrees are set the theme reverts to sphinx's usual local toctree.

It's important to note that if you don't follow the same styling for your rST headers across
your documents, the toctree will misbuild, and the resulting menu might not show the correct
depth when it renders.

Also note that the table of contents is set with ``includehidden=true``. This allows you
to set a hidden toc in your index file with the hidden_ property that will allow you
to build a toc without it rendering in your index.

By default, the navigation will "stick" to the screen as you scroll. However if your toc
is vertically too large, it revert to static positioning. To disable the sticky nav
alltogether change the setting in ``conf.py``.

Contributing or modifying the theme
===================================

The sphinx_testmunk_theme is primarily a sass_ project that requires a few other sass libraries. It uses
using bower_ to manage these dependencies and sass_ to build the css. It comes with
a very nice set of grunt_ operations that will not only load these dependecies, but watch
for changes, rebuild the sphinx demo docs and build a distributable version of the theme.
The bad news is this means you'll need to set up your environment similar to that
of a front-end developer (vs. that of a python developer). That means installing node and ruby.

Set up your environment
-----------------------

1. Install sphinx_ into a virtual environment.

.. code::

    pip install sphinx

2. Install sass

.. code::

    gem install sass

2. Install node, bower and grunt.

.. code::

    // Install node
    brew install node

    // Install bower and grunt
    npm install -g bower grunt-cli

    // Now that everything is installed, let's install the theme dependecies.
    npm install

Now that our environment is set up, make sure you're in your virtual environment, go to
this repository in your terminal and run grunt:

.. code::

    grunt

This default task will do the following **very cool things that make it worth the trouble**.

1. It'll install and update any bower dependencies.
2. It'll run sphinx and build new docs.
3. It'll watch for changes to the sass files and build css from the changes.
4. It'll rebuild the sphinx docs anytime it notices a change to .rst, .html, .js
   or .css files.

Updating the theme for the testmunk/docs repository
===================================================

Run `grunt` to make sure the theme is built. Copy the files from the `sphinx_rtd_theme/` 
folder in the `sphinx_testmunk_theme` repository into the `_themes/sphinx_testmunk_theme/`
folder in the `docs` repository. Build the docs locally to make sure they look correct and
build with no errors, and then commit and push the changes.



