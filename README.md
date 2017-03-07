# 3RWW Atlas Docs built with *mkdocs*

This directory contains the 3RWW Atlas Documentation source files, written in markdown and configured with YAML for use with [mkdocs](http://www.mkdocs.org/)

# Conventions

Documentation is written markdown. File-naming conventions are as follows:

* **Help.** `help_` prefixed files are for general help documentation, and serve to document the functionality of the app independent from any workflow.
* **Guides.** 'guide_' prefixed files are for workflow-specific user guides, intended to walk users through the button clicks needed to get certain information or create something.

# Style

* `extra.css` includes custom 3RWW styling elements that supplant a few underlying default mkdocs Bootstrap styling parameters (e.g., color, fonts). 

## Usage

### Serve

From the command line, navigate to the directory and enter:
`mkdocs serve`

Open `http://localhost:8000` in your browser to view a live preview of the documentation. This will auto-refresh with changes to the underlying markdown and YAML files.

### Build for Deployment

From the command line, navigate to the directory  and enter:
`mkdocs build`

This will generate all the files needed to serve up the full static help doucmentation site.

A default build directory is set for our particular project folder structure. `D:\Dropbox\CivicMapper\Projects\3RWW\Atlas\Atlas Docs\atlas_mkdocs_build`

Note that the build directory as served includes an additional page (*guide_rsi.html*) that exists only for a client-side redirect from the mds.3riverswetweather.org. This page is not generated from `mkdocs build`.

The build is manually deployed using FTP to a `mds.3riverswetweather.org` folder.
