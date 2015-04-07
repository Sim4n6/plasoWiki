To download the latest version of Plaso you'll need to install the git tools:
```
sudo apt-get install git
```

Checkout the plaso source from the git repo:
```
git clone https://github.com/log2timeline/plaso.git
```

To be able to run the plaso [development release](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap) on Ubuntu or equivalent you'll have to have installed the [dependencies](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu).

Check if you have all the dependencies installed and have the right minimum version:
```
python utils/check_dependencies.py
```

**Note that some dependencies are actively under development and can be frequently updated, therefore we recommend checking the status of the dependencies regularly.**

## Update frequently
If you really want to run the development release, aka "Bleeding Edge", make sure to update frequently.

To update plaso:
```
git pull origin master
```

If you are using a "github fork" your origin is pointing your fork not the main plaso git repo:
```
git remote -v
origin	https://github.com/log2timeline/plaso (fetch)
origin	https://github.com/log2timeline/plaso (push)
```

Add an upstream remote that you can use to sync your fork:
```
git remote add upstream https://github.com/log2timeline/plaso.git
git pull upstream master
```

**TODO: add note and link to devtools about maintaining dependencies.**

## Development tools
If you intend to do development on plaso you'll also need to install some development tools:

* PyLint
* Python Mock 

### PyLint
We recommend PyLint 1.4.0 or later. 

Remove any older version of PyLint.
```
sudo apt-get remove pylint
```

Install the necessary dependencies for building PyLint:
```
sudo aptitude install python-epydoc graphviz python-unittest2
```

Download and build the python-logilab-common Debian package:
```
hg clone http://hg.logilab.org/logilab/common
cd common
dpkg-buildpackage -rfakeroot
cd ..
```

Since you're building from development branch it can be possible that you need to disable any failing tests.
Either report these as bugs to the PyLint project or fix them yourself.

Download and build the python-astroid Debian package:
```
hg clone https://bitbucket.org/logilab/astroid
cd astroid
dpkg-buildpackage -rfakeroot
cd ..
```

Download and build the pylint Debian package:
```
hg clone https://bitbucket.org/logilab/pylint
cd pylint
dpkg-buildpackage -rfakeroot
cd ..
```

Install the python-logilab-common, python-astroid and pylint Debian packages:
```
sudo dpkg -i python-logilab-common_0.60.0-1_all.deb python-astroid_1.0.1-1_all.deb pylint_1.0.0-1_all.deb
```

### Python Mock
To install Python Mock run:
```
sudo apt-get install python-mock
```

## Creating a packaged release
**TODO: add description.**

### Source dpkg
Copy the dpkg files to a debian sub directory:
```
mkdir debian && cp config/dpkg/* debian
```

Update the dpkg changelog:
```
export NAME="Log2Timeline";
export EMAIL="log2timeline-dev@googlegroups.com";
dch -v 1.2.1-dev-20150507-1ppa1~trusty --distribution trusty --urgency low "Modifications for PPA release."
```

Build a source package:
```
debuild -S -sa
```

Upload to gift:
```
dput ppa:gift/testing plaso-python_1.2.1-dev-20150507-1ppa1~trusty_source.changes
```