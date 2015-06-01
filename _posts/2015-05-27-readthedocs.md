---
layout: post
title:  Single documentation for multiple git repositories using Read the Docs
date:   2015-05-27 15:30:00
modified: 2015-06-01
description:
headline:
tags: [git,readthedocs]
category: Git and related services
imagefeature:
mathjax:
chart:
comments: true
share: true
---

Sometimes it is more convenient to organise a project in multiple repositories, such as
in the case it is made of many self-consistent parts which could be used separately.
Therefore, each component needs its documentation and at the same time the overall documentation
should remain for the whole project. Since the documentation source files (I am supposing you
  are using RestructuredText or MarkDown to document your code)
are distributed among different the repositories the main project needs to refer to
these files without duplications. This allows the developers
to update the documentation of the components they are working on directly and
without interfere with others but at the same time generate the documentation for the
whole project.

If you are using Sphinx or a service like [Read the Docs](http://https://readthedocs.org)
which use it behind the scene, it is possible to easily generate the overall documentation.
The first step is to create a new repository for the documentation and add as submodules
the repositories containing the documentation you want to include.

    git submodule add <repository_url>

In case of Read the Docs with public repositories it is important to note that the repository has to be
accessible without authentication. Therefore, when you retrieve the link from GitHub
this has to be with the ``http`` or ``https`` protocol, if you use the ``git``
protocol for ``ssh`` connection the documentation will not be created correctly.

After you have add all the submodules you have to create an ``index.rst`` file in
the top level directory of this new package. The file has to contain the ``toctree``
element of Sphinx. This will provide the list of document to include during the
build process and will generate the TOC. An example if index.rst is:

    ================
    My Documentation
    ================


    .. toctree::
       :maxdepth: 2

       submodule1/docs/index
       submodule2/docs/index

You have to replace the name of the submodule and the path to the index file with
the correct one. Following the toctree you could add some text describing the
project as a whole or have this in a separate file.

Commit the repository to GitHub and re-build the documentation from Read the Docs
(if it is not triggered by the commit) or on command line with Sphinx. You should
get the complete documentation.

When a submodule is updated you need to update the submodule reference in your
repository because it references a specific commit. To update the submodules do
the pull request in each submodule directory, commit and push back to the repository.

Of course it is possible to customise the TOC with many parameters,
for more information see the [Sphinix documentation on toctree](http://sphinx-doc.org/markup/toctree.html).
