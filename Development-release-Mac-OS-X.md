To download the latest version of Plaso you'll need to install the git tools: http://git-scm.com/downloads

Checkout the plaso source from the git repo:
```
git clone https://github.com/log2timeline/plaso.git
```

To be able to run the plaso [development release](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap) on Mac OS X you'll have to have installed the [dependencies](https://github.com/log2timeline/plaso/wiki/Dependencies-Mac-OS-X).

Check if you have all the dependencies installed and have the right minimum version:
```
./utils/check_dependencies.py
```

**Note that some dependencies are actively under development and can be frequently updated, therefore we recommend checking the status of the dependencies regularly.**

## Development tools
If you intend to do development on plaso you'll also need to install some development tools:

* PyLint

### PyLint
We recommend PyLint 1.0.0 or later.

**TODO: add description.**

## Creating a packaged release
If all dependency packages have been compiled accordingly make sure they are placed in a sub directory of the plaso source directory named:
```
dependencies
```

To create a distribution package run:
```
./config/macosx/make_dist.sh
```

This will create a file named: plaso-${PLASO_VERSION}_macosx-10.10.dmg at the same level as the plaso source directory.

Note that you can pass this script an additional version suffix e.g. rc1.
```
./config/macosx/make_dist.sh rc1
```
