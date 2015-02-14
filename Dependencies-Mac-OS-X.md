**TODO: work in progress migrating from: https://sites.google.com/a/kiddaland.net/plaso/developer/building-the-tool/mac-os-x**

This page contains detailed instructions on how to build and install dependencies on Mac OS X.

There are multiple ways to install the dependencies on Ubuntu:

* Using the [log2timeline devtools](https://github.com/log2timeline/devtools) to batch build most of the dependencies;
* Manual build of the dependencies.

## Batch build
**TODO describe**

## Manual build
### Build essentials
Make sure the necessary building tools and development packages are installed on the system:

* Python 2.7 (or a later 2.x version)
* Python setuptools or distutils
* XCode
  * Command Line Tools

### Bencode
Download the latest source package from: https://pypi.python.org/pypi/bencode/1.0.

To build pkg files run the following command from the build root directory:
```
tar xvfz bencode-1.0.tar.gz 
cd bencode-1.0
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.bencode --version 1.0 --ownership recommended bencode.1.0.pkg
```

To install the required pkg files run:
```
sudo installer -target / -pkg bencode.1.0.pkg
```

### Binplist
Download the latest source package from: https://code.google.com/p/binplist/downloads/list

To build pkg files run the following command from the build root directory:
```
tar -zxvf binplist-0.1.4.tar.gz 
cd binplist-0.1.4/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.google.code.p.binplist --version 0.1.4 --ownership recommended binplist.1.0.4.pkg
```

To install the required pkg files run:
```
sudo installer -target / -pkg binplist.1.0.4.pkg
```

### Construct
Construct is dependent on six see the instructions below how to build and install six.

Download the latest 2.x source package from: https://pypi.python.org/pypi/construct/2.5.2

To build pkg files run the following command from the build root directory:
```
tar xfvz construct-2.5.2.tar.gz
cd construct-2.5.2
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.construct --version 2.5.2 --ownership recommended construct.2.5.2.pkg
```

To install the required pkg files run:
```
sudo installer -target / -pkg construct.2.5.2.pkg
```

### six
Download the latest 1.x source package from: https://pypi.python.org/pypi/six#downloads

To build pkg files run the following command from the build root directory:
```
tar xfvz six-1.6.1.tar.gz
cd six-1.6.1
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.six --version 1.6.1 --ownership recommended six.1.6.1.pkg
```

To install the required pkg files run:
```
sudo installer -target / -pkg six.1.6.1.pkg
```
