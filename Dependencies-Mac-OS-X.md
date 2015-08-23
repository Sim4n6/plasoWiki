This page contains detailed instructions on how to build and install dependencies on Mac OS X.

There are multiple ways to install the dependencies on Ubuntu:

* Prepackaged dependencies;
* Using the [log2timeline devtools](https://github.com/log2timeline/devtools) to batch build most of the dependencies;
* Manual build of the dependencies.

**Note that if you have a non-Apple version of Python installed e.g. downloaded from Python.org, MacPorts or equivalent. You may very likely will have issues with version mismatches between the Apple versions and the non-Apple version of Python. It is therefore recommended to stick with the Apple versions of Python.**

## Prepackaged dependencies
Prepackaged versions of the dependencies can be found here: https://github.com/log2timeline/l2tbinaries

The l2tdevtools project provides [an update script](https://github.com/log2timeline/l2tdevtools/wiki/Update-script) to ease the process of keeping the dependencies up to date. To run:
```
PYTHONPATH=. python tools/update.py
```

## Batch build
Set up the [l2tdevtools build script](https://github.com/log2timeline/l2tdevtools/wiki/Build-script) and run:
```
PYTHONPATH=. python tools/build.py pkg
```

**Note that the build script is currently still work in progress, but it will build most of the dependencies.**

## Manual build
It is impossible for us to support all flavors of Mac OS X out there, so if you want smooth sailing, we recommend sticking with the supported version or live with the fact that a manual build of the dependencies can be a tedious task.

For ease of maintenance the following instructions use as much pkg packages as possible. Note that the resulting pkg packages are not intended for public redistribution.

Alternative installation methods like installing directly from source, using easy_install or pip are [not recommended](https://stackoverflow.com/questions/3220404/why-use-pip-over-easy-install) because when not maintained correctly they can mess up your setup more easily than using rpm packages.

First create a build root directory:
```
mkdir plaso-build/
```

### Build essentials
Make sure the necessary building tools and development packages are installed on the system:

* Python 2.7 (or a later 2.x version)
* Python setuptools or distutils
* XCode
  * Command Line Tools
* Cython

#### Cython
Download the latest source package from: http://cython.org/#download

To build pkg files run the following command from the build root directory:
```
tar -zxvf Cython-0.23.1.tar.gz
cd Cython-0.23.1
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.cython.cython --version 0.23.1 --ownership recommended ../cython-0.23.1.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg cython-0.23.1.pkg
```

### Python modules
The following instructions apply to the following dependencies:

Name | Download URL | Identifier | Comments | Dependencies
--- | --- | --- | --- | --- 
artifacts | https://github.com/ForensicArtifacts/artifacts/releases | com.github.ForensicArtifacts.artifacts | |

#### Building a PKG
To build pkg files run the following commands from the build root directory.

First extract the package:
```
tar -zxvf package-1.0.0.tar.gz 
```

Next change into the package source directory and have setup.py build a binary distribution (bdist).
```
cd package-1.0.0/
python setup.py bdist
```

This will create a tar.gz in the dist sub directory e.g.:
```
dist/package-1.0.0.macosx-10.10-intel.tar.gz
```

Next create a pgk
```
mkdir dist/tmp && cd dist/tmp && tar xfvz ../package-1.0.0*.tar.gz && cd ../..
pkgbuild --root dist/tmp --identifier $IDENTIFIER --version 1.0.0 --ownership recommended ../package-1.0.0.pkg
cd ..
```

Where ` $IDENTIFIER` contains an unique identifier for the package e.g. com.github.ForensicArtifacts.artifacts for artifacts.

To install the required pkg files run:
```
sudo installer -target / -pkg package-1.0.0.pkg
```

### Bencode
Download the latest source package from: https://pypi.python.org/pypi/bencode/1.0

To build pkg files run the following command from the build root directory:
```
tar xvfz bencode-1.0.tar.gz 
cd bencode-1.0/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.bencode --version 1.0 --ownership recommended ../python-bencode-1.0.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-bencode-1.0.pkg
```

### Binplist
Download the latest source package from: https://github.com/google/binplist/releases

To build pkg files run the following command from the build root directory:
```
tar -zxvf binplist-0.1.5.tar.gz 
cd binplist-0.1.5/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.github.google.binplist --version 0.1.5 --ownership recommended ../python-binplist-0.1.5.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-binplist-0.1.5.pkg
```

### Construct
Construct is dependent on six see the instructions below how to build and install six.

Download the latest 2.x source package from: https://pypi.python.org/pypi/construct/2.5.2

To build pkg files run the following command from the build root directory:
```
tar xfvz construct-2.5.2.tar.gz
cd construct-2.5.2/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.construct --version 2.5.2 --ownership recommended ../python-construct-2.5.2.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-construct-2.5.2.pkg
```

### dateutil
Download the latest source package from: https://github.com/dateutil/dateutil/releases

To build pkg files run the following command from the build root directory:
```
tar xfvz dateutil-2.4.1.tar.gz
cd dateutil-2.4.1/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.github.dateutil.dateutil --version 2.4.1 --ownership recommended ../python-dateutil-2.4.1.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-dateutil-2.4.1.pkg
```

### dfVFS
The dfVFS build instructions can be found [here](https://github.com/log2timeline/dfvfs/wiki/Building). Note that for dfVFS to function correctly several dependencies, like pytsk, mentioned later in a section of this page, are required.

Download the latest source package from: https://github.com/log2timeline/dfvfs/releases

To build pkg files run the following command from the build root directory:
```
tar xfvz dfvfs-20140219.tar.gz
cd dfvfs-20140219/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
mkdir -p dist/tmp/usr/share/doc/dfvfs
cp AUTHORS ACKNOWLEDGEMENTS LICENSE dist/tmp/usr/share/doc/dfvfs
pkgbuild --root dist/tmp --identifier com.github.log2timeline.dfvfs --version 20140219 --ownership recommended python-dfvfs-20140219.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-dfvfs-20140219.pkg
```

### DPKT
Download the latest source package from: https://pypi.python.org/pypi/dpkt

To build pkg files run the following command from the build root directory:
```
tar xfvz dpkt-1.8.6.tar.gz
cd dpkt-1.8.6
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.google.code.p.dpkt --version 1.8.6 --ownership recommended ../python-dpkt-1.8.6.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-dpkt-1.8.6.pkg
```

### IPython
Download the latest source package from: https://github.com/ipython/ipython/releases

To build pkg files run the following command from the build root directory:
```
tar xfvz ipython-1.2.1.tar.gz
cd ipython-1.2.1
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
mkdir -p dist/tmp/usr/share/doc/ipython
cp COPYING.txt dist/tmp/usr/share/doc/ipython
pkgbuild --root dist/tmp --identifier org.github.ipython.ipython --version 1.2.1 --ownership recommended ../ipython-1.2.1.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg ipython-1.2.1.pkg
```

### Hachoir
Download the latest source package from: https://bitbucket.org/haypo/hachoir/wiki/Install/source

You'll need:

* hachoir-core-1.3.3.tar.gz
* hachoir-parser-1.3.4.tar.gz
* hachoir-metadata-1.3.3.tar.gz

To build pkg files run the following command from the build root directory:
```
tar xfvz hachoir-core-1.3.3.tar.gz
cd hachoir-core-1.3.3
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.bitbucket.hachoir.core --version 1.3.3 --ownership recommended ../python-hachoir-core-1.3.3.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-hachoir-core-1.3.3.pkg
```

To build pkg files run the following command from the build root directory:
```
tar xfvz hachoir-parser-1.3.4.tar.gz
cd hachoir-parser-1.3.4
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.bitbucket.hachoir.parser --version 1.3.4 --ownership recommended ../python-hachoir-parser-1.3.4.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-hachoir-parser-1.3.4.pkg
```

To build pkg files run the following command from the build root directory:
```
tar xfvz hachoir-metadata-1.3.3.tar.gz
cd hachoir-metadata-1.3.3
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.bitbucket.hachoir.metadata --version 1.3.3 --ownership recommended ../python-hachoir-metadata-1.3.3.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-hachoir-metadata-1.3.3.pkg
```

### Libprotobuf and Python-bindings
Libprotobuf is dependent on python-gflags see the instructions below how to build and install python-gflags.

Download the latest 2.x source package from: https://github.com/google/protobuf/releases

To build pkg files run the following command from the build root directory:
```
tar xfvz protobuf-2.6.1.tar.gz
cd protobuf-2.6.1
./configure --prefix=/usr
make
make install DESTDIR=$PWD/osx-pkg
pkgbuild --root osx-pkg --identifier com.github.google.protobuf --version 2.6.1 --ownership recommended ../protobuf-2.6.1.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg protobuf-2.6.1.pkg
```

To build pkg files run the following command from the build root directory:
```
cd protobuf-2.6.1/python
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.github.google.python-protobuf --version 2.6.1 --ownership recommended ../../python-protobuf-2.6.1.pkg
cd ../../
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-protobuf-2.6.1.pkg
```

### libyal
The following instructions apply to the following dependencies:

* [libbde](https://github.com/libyal/libbde)
* [libesedb](https://github.com/libyal/libesedb)
* [libevt](https://github.com/libyal/libevt)
* [libevtx](https://github.com/libyal/libevtx)
* [libewf](https://github.com/libyal/libewf)
* [libfwsi](https://github.com/libyal/libfwsi)
* [liblnk](https://github.com/libyal/liblnk)
* [libmsiecf](https://github.com/libyal/libmsiecf)
* [libolecf](https://github.com/libyal/libolecf)
* [libqcow](https://github.com/libyal/libqcow)
* [libregf](https://github.com/libyal/libregf)
* [libsigscan](https://github.com/libyal/libsigscan)
* [libsmdev](https://github.com/libyal/libsmdev)
* [libsmraw](https://github.com/libyal/libsmraw)
* [libvhdi](https://github.com/libyal/libvhdi)
* [libvmdk](https://github.com/libyal/libvmdk)
* [libvshadow](https://github.com/libyal/libvshadow)

Install the following dependencies for building libyal:

* zlib
* bzip2
* dokan

**TODO: describe building dependencies.**

Since the build process for the libyal libraries is very similar, the following paragraph provides building libevt as an example. For more details see the build instructions of the individual projects e.g. https://github.com/libyal/libevt/wiki/Building.

Note that there is also a script to batch build the libyal dependencies more information here: https://code.google.com/p/libyal/wiki/LibyalBuild

#### Example: libevt and Python-bindings
Download the latest source package from: https://github.com/libyal/libevt/releases

To build pkg files run the following command from the build root directory:
```
tar xfvz libevt-alpha-20130415.tar.gz
cd libevt-alpha-20130415
./configure --disable-dependency-tracking --prefix=/usr/ --enable-python --with-pyprefix
make && make install DESTDIR=$PWD/osx-pkg
mkdir -p $PWD/osx-pkg/usr/share/doc/libevt
cp LICENSE $PWD/osx-pkg/usr/share/doc/libevt
pkgbuild --root osx-pkg --identifier com.github.libyal.libevt --version 20130415 --ownership recommended ../libevt-20130415.pkg
```

To install the required pkg files run:
```
sudo installer -target / -pkg libevt-20130415.pkg
```

### Libyaml and Python-bindings
Download the latest source package from: http://pyyaml.org/download/libyaml/ (or http://pyyaml.org/wiki/LibYAML)

To build pkg files run the following command from the build root directory:
```
tar xfvz yaml-0.1.6.tar.gz
cd yaml-0.1.6
./configure --prefix=/usr
make
make install DESTDIR=$PWD/osx-pkg
pkgbuild --root osx-pkg --identifier org.pyyaml.yaml --version 0.1.6 --ownership recommended ../libyaml-0.1.6.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg libyaml-0.1.6.pkg
```

Download the latest source package from: http://pyyaml.org/wiki/PyYAML

To build pkg files run the following command from the build root directory:
```
tar xfvz PyYAML-3.11.tar.gz
cd PyYAML-3.11/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.pyyaml.yaml.python --version 3.11 --ownership recommended ../python-yaml-3.11.pkg
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-yaml-3.11.pkg
```

### Pefile
Download the latest source package from: https://github.com/erocarrera/pefile/releases

**TODO describe manual fixes**

To build pkg files run the following command from the build root directory:
```
tar -zxvf pefile-1.2.10-139.tar.gz
cd pefile-pefile-1.2.10-139/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.github.erocarrer.pefile --version 1.2.10-139 --ownership recommended ../python-pefile-1.2.10-139.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-pefile-1.2.10-139.pkg
```

### Psutil
Download the latest source package from: https://pypi.python.org/pypi/psutil/#downloads

To build pkg files run the following command from the build root directory:
```
tar xvfz psutil-1.2.1.tar.gz
cd psutil-1.2.1/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
mkdir -p dist/tmp/usr/share/doc/psutil
cp LICENSE dist/tmp/usr/share/doc/psutil
pkgbuild --root dist/tmp --identifier org.python.pypi.psutil --version 1.0 --ownership recommended ../python-psutil-1.2.1.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-psutil-1.2.1.pkg
```

### Pyparsing
Download the latest source package from: http://sourceforge.net/projects/pyparsing/files/

To build pkg files run the following command from the build root directory:
```
tar xfvz pyparsing-2.0.3.tar.gz 
cd pyparsing-2.0.3/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier net.sourceforge.pyparsing --version 2.0.3 --ownership recommended ../python-pyparsing-2.0.3.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-pyparsing-2.0.3.pkg
```

### pyreadline
Download the latest 1.x source package from: https://pypi.python.org/pypi/pyreadline/#downloads

**TODO describe**

#### python-gflags
Download the latest source package from: https://github.com/google/python-gflags/releases

To build pkg files run the following command from the build root directory:
```
tar xfvz python-gflags-2.0.tar.gz
cd python-gflags-python-gflags-2.0/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.github.google.python-gflags --version 2.0 --ownership recommended ../python-gflags-2.0.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-gflags-2.0.pkg
```

### pytz
Download the latest source package from: http://pypi.python.org/pypi/pytz/#downloads

To build pkg files run the following command from the build root directory:
```
tar xfvz pytz-2014.10.tar.gz
cd pytz-2014.10/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.pytz --version 2014.10 --ownership recommended ../python-pytz-2014.10.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-pytz-2014.10.pkg
```

### requests
Download the latest source package from: https://github.com/kennethreitz/requests/releases

**Make sure to click on:** "Show # newer tags"

To build pkg files run the following command from the build root directory:
```
mv v2.7.0.tar.gz requests-2.7.0.tar.gz
tar xfvz requests-2.7.0.tar.gz
cd requests-2.7.0/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.github.kennethreitz.requests --version 2.7.0 --ownership recommended ../python-requests-2.7.0.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-requests-2.7.0.pkg
```

### six
Download the latest 1.x source package from: https://pypi.python.org/pypi/six#downloads

To build pkg files run the following command from the build root directory:
```
tar xfvz six-1.6.1.tar.gz
cd six-1.6.1/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.six --version 1.6.1 --ownership recommended ../python-six-1.6.1.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-six-1.6.1.pkg
```

### Sleuthkit and Pytsk
The build and install Sleuthkit and Pytsk see:

* https://github.com/py4n6/pytsk/wiki/Building-SleuthKit#using-mac-os-x-pkgbuild
* https://github.com/py4n6/pytsk/wiki/Building#using-mac-os-x-pkgbuild

### SQLite
**TODO describe**

### Optional dependencies for Elastic Search
#### PyElasticsearch
Download the latest source package from: https://github.com/rhec/pyelasticsearch/releases

To build pkg files run the following command from the build root directory:
```
tar zxfv pyelasticsearch-1.0.tar.gz
cd pyelasticsearch-1.0/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.github.pyelasticsearch.pyelasticsearch --version 1.0 --ownership recommended ../python-pyelasticsearch-1.0.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-pyelasticsearch-1.0.pkg
```

#### XlsxWriter
Download the latest source package from: https://github.com/jmcnamara/XlsxWriter/releases

To build pkg files run the following command from the build root directory:
```
tar zxfv XlsxWriter-RELEASE_0.7.3.tar.gz
cd XlsxWriter-RELEASE_0.7.3/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.github.jmcnamara.xlsxwriter --version 0.7.3 --ownership recommended ../python-xlsxwriter-0.7.3.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-xlsxwriter-1.0.pkg
```