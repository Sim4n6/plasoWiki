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
Download the latest source package from: https://pypi.python.org/pypi/bencode/1.0

To build pkg files run the following command from the build root directory:
```
tar xvfz bencode-1.0.tar.gz 
cd bencode-1.0/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.bencode --version 1.0 --ownership recommended ../python-bencode.1.0.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-bencode.1.0.pkg
```

### Binplist
Download the latest source package from: https://code.google.com/p/binplist/downloads/list

To build pkg files run the following command from the build root directory:
```
tar -zxvf binplist-0.1.4.tar.gz 
cd binplist-0.1.4/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.google.code.p.binplist --version 0.1.4 --ownership recommended ../python-binplist.1.0.4.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-binplist.1.0.4.pkg
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
pkgbuild --root dist/tmp --identifier org.python.pypi.construct --version 2.5.2 --ownership recommended ../python-construct.2.5.2.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-construct.2.5.2.pkg
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
pkgbuild --root dist/tmp --identifier com.github.log2timeline.dfvfs --version 20140219 --ownership recommended python-dfvfs.20140219.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-dfvfs.20140219.pkg
```

### DPKT
Download the latest source package from: https://code.google.com/p/dpkt/downloads/list

To build pkg files run the following command from the build root directory:
```
tar xfvz dpkt-1.8.tar.gz
cd dpkt-1.8
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier com.google.code.p.dpkt --version 1.8 --ownership recommended ../python-dpkt.1.8.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-dpkt.1.8.pkg
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
pkgbuild --root osx-pkg --identifier org.pyyaml.yaml --version 0.1.6 --ownership recommended ../libyaml.0.1.6.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg libyaml.0.1.6.pkg
```

Download the latest source package from: http://pyyaml.org/wiki/PyYAML

To build pkg files run the following command from the build root directory:
```
tar xfvz PyYAML-3.11.tar.gz
cd PyYAML-3.11/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.pyyaml.yaml.python --version 3.11 --ownership recommended ../python-yaml.3.11.pkg
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-yaml.3.11.pkg
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
pkgbuild --root dist/tmp --identifier net.sourceforge.pyparsing --version 2.0.3 --ownership recommended ../python-pyparsing.2.0.3.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-pyparsing.2.0.3.pkg
```

### six
Download the latest 1.x source package from: https://pypi.python.org/pypi/six#downloads

To build pkg files run the following command from the build root directory:
```
tar xfvz six-1.6.1.tar.gz
cd six-1.6.1/
python setup.py bdist
mkdir dist/tmp && cd dist/tmp && tar xfvz ../*gz && cd ../..
pkgbuild --root dist/tmp --identifier org.python.pypi.six --version 1.6.1 --ownership recommended ../python-six.1.6.1.pkg
cd ..
```

To install the required pkg files run:
```
sudo installer -target / -pkg python-six.1.6.1.pkg
```
