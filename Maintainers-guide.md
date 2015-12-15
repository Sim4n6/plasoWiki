This page contains information relevant to plaso maintainers.

## Mailing list
Maintainers mailing list: log2timeline-maintainers@googlegroups.com

## Maintainer guidelines

* [Feature requests and bug reports](https://github.com/log2timeline/plaso/wiki/Feature-requests-and-bug-reports)

## Maintainer tools
If you intend to help maintain on plaso you'll also need to install the following tools:

* Sphinx-doc

### Sphinx-doc
#### Fedora Core
To install sphinx-doc on Fedora Core run:
```
sudo yum install python-sphinx-doc
```

### Mac OS -X
To install sphinx-doc on Mac OS-X run:

**TODO: add description.**

### Ubuntu
To install sphinx-doc on Ubuntu run:
```
sudo apt-get install python-sphinx
```

### Windows
To install sphinx-doc on Windows run:

**TODO: add description.**

## Generating plaso wiki pages
Checkout the plaso wiki pages:
```
git clone https://github.com/log2timeline/plaso.wiki.git
```

To generate the [parser and plugins](https://github.com/log2timeline/plaso/wiki/Parsers-and-plugins) page:
```
PYTHONPATH=plaso plaso/tools/log2timeline.py --use-markdown --parsers list > plaso.wiki/Parsers-and-plugins.md
```

Commit and push the changes to the wiki pages.

## Generating API docs with Sphinx-doc
Plaso uses [sphinx](http://sphinx-doc.org/) to generate API documentation. The plaso configuration uses the [autodoc](http://sphinx-doc.org/ext/autodoc.html) plugin for automatic documentation generation, and the [napoleon](http://sphinxcontrib-napoleon.readthedocs.org/en/latest/sphinxcontrib.napoleon.html) plugin to read our “Google style” docstrings. 

The configuration is stored [here](https://github.com/log2timeline/plaso/blob/master/docs/conf.py) and the actual HTML documentation is built and stored with readthedocs.org, as described below.
The [merge_submit script](https://github.com/log2timeline/plaso/blob/master/utils/merge_submit.sh), which is run by the maintainers, triggers a [sphinx-apidoc](http://sphinx-doc.org/man/sphinx-apidoc.html) run, which will generate reStructured text files which readthedocs will use to generate the HTML docs. 

One little wrinkle in this pipeline is that to generate the API docs, readthedocs needs to `import` each python file. This will fail if it can't import all dependencies, and it's not possible to install native dependencies on readthedocs. The Sphinx configuration tries to take care of this by automatically mocking the dependencies in [dependencies.py](https://github.com/log2timeline/plaso/blob/master/plaso/dependencies.py) but it may be necessary on occasion to add a dependency explicitly to the sphinx config.

If you'd like to test the full HTML documentation build locally, not on readthedocs, cd to the ```docs``` directory and run ```make html```.

## Readthedocs.org
The plaso documentation on [readthedocs.org](https://readthedocs.org/projects/plaso/) is mirrored off the [plaso wiki](https://github.com/log2timeline/plaso/wiki). The wiki git repo does not have the same webhooks as the plaso source git repo and thus we rely on a manual build trigger in the [merge_submit script](https://github.com/log2timeline/plaso/blob/master/utils/merge_submit.sh) to refresh the documentation.

The build of the [plaso-api documentation](https://readthedocs.org/projects/plaso-api/) is triggered by github service integration with readthedocs.

### Markdown compatibility

Define links as:
```
[description](URL)
```
Note that having a space between `]` and `(` breaks on readthedocs.

## Creating a packaged release
### Mac OS-X
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

### Ubuntu source dpkg for gift PPA
Copy the dpkg files to a debian sub directory:
```
mkdir debian && cp -r config/dpkg/* debian
```

Work around for a Unicode bug on launchpad:
```
mv test_data/ímynd.dd test_data/image.dd
IFS="
"; for FILE in `grep -r ímynd.dd | sed 's/:.*$//'`; do sed 's/ímynd.dd/image.dd/g' -i $FILE; done
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

Upload to the testing track of gift:
```
dput ppa:gift/testing plaso-python_1.2.1-dev-20150507-1ppa1~trusty_source.changes
```

### Windows
To create a Windows packaged release from the development release you also need:

* PyInstaller

#### PyInstaller
Download the latest source from:
```
git clone -b master git://github.com/pyinstaller/pyinstaller.git
```

**Note that setup.py build and install is currently disabled, so we need to run PyInstaller from its download directory.**

##### Rebuilding the PyInstaller bootloader
By default PyInstaller is code compatible with Windows XP SP2 (5.1). If you need to support a Windows version earlier you'll need to recompile the PyInstaller "bootloader" with Visual Studio 2008. Note that Visual Studio 2010 is not compatible with Windows 2000.

```
cd PyInstaller\bootloader
C:\Python27\python.exe waf configure build install
```

##### Microsoft Visual C++ 2010 Redistributable Package
If you're building with Visual Studio note that for some reason PyInstaller does not include the Microsoft Visual C++ 2010 run-time DLLs you can find them here:

* [Microsoft Visual C++ 2010 Redistributable Package (x86)](http://www.microsoft.com/en-us/download/details.aspx?id=5555)
* [Microsoft Visual C++ 2010 Redistributable Package (x64)](http://www.microsoft.com/en-us/download/details.aspx?id=14632)

#### Preparations
If you are intending to distribute the packaged release make sure to do the following steps:

`1`. Make sure the dependencies are up to date.

`2`. Remove code that cannot be redistributed due to a license restriction, by running:
```
sh utils/prep_dist.sh
```

**Note that you'll need to run this under Cygwin or equivalent.**

`3`. Distribute a copy of:
```
AUTHORS
ACKNOWLEDGEMENT
LICENSE
config\licenses\*
```

#### Packaging
First check if the PyInstaller build script: config\windows\make.bat is configured correctly for your build environment.

From the plaso source directory run the following commands:

To build plaso with PyInstaller run:
```
config\windows\make.bat
```

This will create sub directories for each of the tools under dist.

To merge all the sub directories into one run:
```
config\windows\make_dist.bat
```

This will create: dist\plaso

To do a very rudimentary test to see if the packaged binaries work run:
```
config\windows\make_check.bat
```

And finally create a zip archive of: dist\plaso