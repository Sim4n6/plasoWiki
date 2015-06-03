This page contains detailed instructions on how to build and install dependencies on Fedora Core. Some of these instructions should also work on Fedora Core like systems like RHEL or OpenSuze.

There are multiple ways to install the dependencies on Fedora Core:

* Using the [log2timeline devtools](https://github.com/log2timeline/devtools) to batch build most of the dependencies;
* Manual build of the dependencies.

## Batch build
Set up the [l2tdevtools build script](https://github.com/log2timeline/l2tdevtools/wiki/Build-script) and run:
```
PYTHONPATH=. python tools/build.py rpm
```

**Note that the build script is currently still work in progress, but it will build most of the dependencies.**

## Manual build
It is impossible for us to support all flavors of Fedora Core out there, so if you want smooth sailing, we recommend sticking with the supported version or live with the fact that a manual build of the dependencies can be a tedious task.

For ease of maintenance the following instructions use as much rpm package files as possible. Note that the resulting rpm files are not intended for public redistribution.

Alternative installation methods like installing directly from source, using easy_install or pip are [not recommended](https://stackoverflow.com/questions/3220404/why-use-pip-over-easy-install) because when not maintained correctly they can mess up your setup more easily than using rpm packages.

First create a build root directory:
```
mkdir plaso-build/
```

Next make sure your installation is up to date:
```
sudo yum update
```

### Build essentials
Make sure the necessary building tools and development packages are installed on the system:
```
sudo yum groupinstall "Development Tools"
sudo yum install gcc-c++ python-devel python-setuptools rpm-build git mercurial
```

**TODO: move to libyal section.**

For some of the dependent packages you also require:
```
sudo yum install flex byacc zlib-devel bzip2-devel openssl-devel fuse-devel
```

### Artifacts
Download the latest source package from: https://github.com/ForensicArtifacts/artifacts/releases

To build rpm files run the following command from the build root directory:
```
tar xvf artifacts-20150409.tar.gz 
cd artifacts-20150409/
python setup.py bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo yum install artifacts-20150409/dist/artifacts-20150409-1.noarch.rpm
```

### Bencode
Download the latest source package from: https://pypi.python.org/pypi/bencode

To build rpm files run the following command from the build root directory:
```
tar xvf bencode-1.0.tar.gz 
cd bencode-1.0/
python setup.py bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo yum install bencode-1.0/dist/bencode-1.0-1.noarch.rpm
```

### Binplist
Download the latest source package from: https://github.com/google/binplist/releases

To build rpm files run the following command from the build root directory:
```
tar xvf binplist-0.1.5.tar.gz 
cd binplist-0.1.5/
python setup.py bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo yum install binplist-0.1.5/dist/binplist-0.1.5-1.noarch.rpm
```

### Construct
Install the following dependencies for building construct:
```
sudo yum install python-six
```

Download the latest 2.x source package from: http://construct.readthedocs.org/en/latest

To build rpm files run the following command from the build root directory:
```
tar xvf construct-2.5.2.tar.gz 
cd construct-2.5.2/
python setup.py bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo yum install construct-2.5.2/dist/construct-2.5.2-1.noarch.rpm
```

**Note if this package could conflict with Fedora distribute version of construct.**

### dateutil
To install dateutil run:
```
sudo yum install python-dateutil
```

### dfVFS
The dfVFS build instructions can be found [here](https://github.com/log2timeline/dfvfs/wiki/Building). Note that for dfVFS to function correctly several dependencies, like pytsk, mentioned later in a section of this page, are required.

Download the latest source package from: https://github.com/log2timeline/dfvfs/releases

To build rpm files run the following command from the build root directory:
```
tar xvf dfvfs-20140219.tar.gz 
cd dfvfs-20140219/
python setup.py bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo rpm -ivh dfvfs-20140219/dist/dfvfs-20140219-1.noarch.rpm
```

### DPKT
**TODO: describe.**

### IPython
By default Fedora 20 comes with IPython 0.13.2. Plaso requires version 1.2.1 or later.

**TODO: describe**

### Hachoir
Download the latest source package from: https://bitbucket.org/haypo/hachoir/wiki/Install/source

You'll need:

* hachoir-core-1.3.3.tar.gz
* hachoir-parser-1.3.4.tar.gz
* hachoir-metadata-1.3.3.tar.gz

To build rpm files run the following command from the build root directory:
```
tar xfv hachoir-core-1.3.3.tar.gz
cd hachoir-core-1.3.3
python setup.py build bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo rpm -ivh hachoir-core-1.3.3/dist/hachoir-core-1.3.3-1.noarch.rpm
```

To build rpm files run the following command from the build root directory:
```
tar xfv hachoir-parser-1.3.4.tar.gz
cd hachoir-parser-1.3.4
python setup.py build bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo rpm -ivh hachoir-parser-1.3.4/dist/hachoir-parser-1.3.4-1.noarch.rpm
```
To build rpm files run the following command from the build root directory:
```
tar xfv hachoir-metadata-1.3.3.tar.gz
cd hachoir-metadata-1.3.3
python setup.py build bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo rpm -ivh hachoir-metadata-1.3.3/dist/hachoir-metadata-1.3.3-1.noarch.rpm
```

### Libprotobuf and Python-bindings
To install libprotobuf and Python-bindings run:
```
sudo yum install protobuf-python
```

If you intend to do development on plaso and change the protobuf definitions, you'll also need to install the protobuf compiler (protoc).
```
sudo yum install protobuf-compiler
```

#### Manual
**TODO: complete this section**

Download the latest 2.x source package from: https://github.com/google/protobuf/releases

Extract the source package:
```
tar xfv protobuf-2.6.1.tar.gz
```

To build the proto compiler (protoc):
```
cd protobuf-2.6.1
./configure
make
```

**TODO: make install works but ideally we create RPMs**

```
cd python/
python setup.py bdist_rpm
cd ../..
```

To install the required rpm files run:
```
sudo yum install protobuf-2.6.1/python/dist/protobuf-2.6.1.x86_64.rpm
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

mv libevt-alpha-20130923.tar.gz libevt-20130923.tar.gz
```
rpmbuild -ta libevt-20130923.tar.gz
```

On a 64-bit version or Fedora 18 this will create the rpm files in the directory:
```
~/rpmbuild/RPMS/x86_64/
```

To install the required rpm files run:
```
sudo rpm -ivh ~/rpmbuild/RPMS/x86_64/libevt-20130923-1.x86_64.rpm ~/rpmbuild/RPMS/x86_64/libevt-python-20130923-1.x86_64.rpm
```

### Libyaml and Python-bindings
To install libyaml and Python-bindings run:
```
sudo yum install libyaml PyYAML
```

### Pefile
**TODO describe**

### Psutil
Download the latest source package from: https://pypi.python.org/pypi/psutil

To build rpm files run the following command from the build root directory:
```
tar xvf psutil-1.2.1.tar.gz 
cd psutil-1.2.1/
python setup.py bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo yum install psutil-1.2.1/dist/psutil-1.2.1.x86_64.rpm
```

### PyParsing
To install the necessary Python-modules run:
```
sudo yum install pyparsing
```

**TODO: describe manual installation**

### pytz
To install the necessary Python-modules run:
```
sudo yum install pytz
```

**TODO: describe manual installation**

### requests
Download the latest source package from: https://github.com/kennethreitz/requests/releases

**Make sure to click on:** "Show # newer tags"

To build rpm files run the following command from the build root directory:
```
mv v2.7.0.tar.gz requests-2.7.0.tar.gz
tar xvf requests-2.7.0.tar.gz 
cd requests-2.7.0/
python setup.py bdist_rpm
cd ..
```

To install the required rpm files run:
```
sudo yum install requests-2.7.0/dist/requests-2.7.0-1.noarch.rpm
```

### Sleuthkit and Pytsk
The build and install Sleuthkit and Pytsk see:

* https://github.com/py4n6/pytsk/wiki/Building-SleuthKit
* https://github.com/py4n6/pytsk/wiki/Building

### Optional dependencies for Elastic Search
#### PyElasticsearch
Download the latest source package from: https://github.com/rhec/pyelasticsearch/releases

**TODO: describe**
