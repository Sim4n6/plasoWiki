This page contains detailed instructions on how to build and install dependencies on Ubuntu. Some of these instructions should also work on Ubuntu like systems like Debian or Linux Mint.

There are multiple ways to install the dependencies on Ubuntu:

* Using the GIFT PPA to install prepackaged versions of the dependencies;
* Using the [log2timeline devtools](https://github.com/log2timeline/devtools) to batch build most of the dependencies;
* Manual build of the dependencies.

## Prepackaged dependencies
**Note that the instructions in this page assume you are running on Ubuntu 12.04 or 14.04. Installing packages from the PPA on other versions and/or distributions is not recommended.**

The [GIFT PPA](https://launchpad.net/~gift), pun intended, contains the necessary packages for running plaso. The GIFT PPA provides the following tracks:

* Stable; track intended for the "packaged release" of plaso and dependencies;
* Bleeding Edge (or Development); track intended for the "development release" of plaso;
* Testing; track intended for testing newly created packages.

For development we recommend using the "Bleeding Edge" track. To add it to your apt configuration run:
```
sudo add-apt-repository ppa:gift/dev
```

To install the dependencies run:
```
sudo apt-get update
sudo apt-get install binplist ipython libbde-python libesedb-python libevt-python libevtx-python libewf-python libfwsi-python liblnk-python libmsiecf-python libolecf-python libqcow-python libregf-python libsigscan-python libsmdev-python libsmraw-python libtsk libvhdi-python libvmdk-python libvshadow-python python-bencode python-coveralls python-construct python-dateutil python-dfvfs python-dpkt python-hachoir-core python-hachoir-metadata python-hachoir-parser python-protobuf python-psutil python-pyparsing python-six python-yaml python-tz pytsk3
```

**Note for the most up to date list of dependencies see: [.travis.yml](https://github.com/log2timeline/plaso/blob/master/.travis.yml)**

For troubleshooting crashes it is recommended to install the following debug symbol packages as well:
```
sudo apt-get install libbde-dbg libbde-python-dbg libesedb-dbg libesedb-python-dbg libevt-dbg libevt-python-dbg libevtx-dbg libevtx-python-dbg libewf-dbg libewf-python-dbg libfwsi-dbg libfwsi-python-dbg liblnk-dbg liblnk-python-dbg libmsiecf-dbg libmsiecf-python-dbg libolecf-dbg libolecf-python-dbg libqcow-dbg libqcow-python-dbg libregf-dbg libregf-python-dbg libsigscan-dbg libsigscan-python-dbg libsmdev-dbg libsmdev-python-dbg libsmraw-dbg libsmraw-python-dbg libvhdi-dbg libvhdi-python-dbg libvmdk-dbg libvmdk-python-dbg libvshadow-dbg libvshadow-python-dbg
```

**TODO complete list of dependencies.**

## Batch build
Set up the [l2tdevtools build script](https://github.com/log2timeline/l2tdevtools/wiki/Build-script) and run:
```
PYTHONPATH=. python scripts/build.py dpkg
```

**Note that the build script is currently still work in progress, but it will build most of the dependencies.**

## Manual build
It is impossible for us to support all flavors of Ubuntu out there, so if you want smooth sailing, we recommend sticking with the supported version or live with the fact that a manual build of the dependencies can be a tedious task.

For ease of maintenance the following instructions use as much deb package files as possible. Note that the resulting deb files are not intended for public redistribution.

Alternative installation methods like installing directly from source, using easy_install or pip are [not recommended](https://stackoverflow.com/questions/3220404/why-use-pip-over-easy-install) because when not maintained correctly they can mess up your setup more easily than using deb packages.

First create a build root directory:
```
mkdir plaso-build/
```

Next make sure your installation is up to date:
```
sudo apt-get update
sudo apt-get upgrade
```

### Build essentials
Make sure the necessary building tools and development packages are installed on the system:
```
sudo apt-get install build-essential autotools-dev libsqlite3-dev python-dev debhelper devscripts fakeroot quilt git mercurial python-dateutil python-setuptools libtool automake
```

### Bencode
Download the 1.0 version from Download the latest source package from: https://pypi.python.org/pypi/bencode and the [Debian packaging files](https://googledrive.com/host/0B30H7z4S52FleW5vUHBnblJfcjg/3rd%20party/build-files/deprecated/bencode-1.0-dpkg.tar.gz).

To build deb files run the following command from the build root directory:
```
tar zxfv bencode-1.0.tar.gz
cd bencode-1.0/
tar zxfv ../bencode-1.0-dpkg.tar.gz
cp -rf dpkg debian
dpkg-buildpackage -rfakeroot
cd ..
```

This will create the following files in the build root directory:
```
python-bencode_1.0-1_all.deb
```

To install the required deb files run:
```
sudo dpkg -i python-bencode_1.0-1_all.deb
```

### binplist
Download the latest source package from: https://code.google.com/p/binplist/downloads/list

To build deb files run the following command from the build root directory:
```
tar xvf binplist-0.1.4.tar.gz 
cd binplist-0.1.4/
cp -rf config/dpkg debian
dpkg-buildpackage -rfakeroot
cd ..
```

This will create the following files in the build root directory:
```
binplist_0.1.4-1_all.deb
```

To install the required deb files run:
```
sudo dpkg -i binplist_0.1.4-1_all.deb
```

### Construct
**Note that Unbuntu 14.04 provides construct 2.5.1 which contains known issues hence we recommend upgrading to version 2.5.2.**

Install the following dependencies for building construct:
```
sudo apt-get install python-six
```

Download the 2.5.2 version from http://construct.readthedocs.org/en/latest/ and the [Debian packaging files](https://googledrive.com/host/0B30H7z4S52FleW5vUHBnblJfcjg/3rd%20party/build-files/deprecated/construct-2.5.2-dpkg.tar.gz).

To build deb files run the following command from the build root directory:
```
tar zxfv construct-2.5.2.tar.gz
cd construct-2.5.2/
tar zxfv ../construct-2.5.2-dpkg.tar.gz
cp -rf dpkg debian
dpkg-buildpackage -rfakeroot
cd ..
```

This will create the following files in the build root directory:
```
python-construct_2.5.2-1_all.deb
```

To install the required deb files run:
```
sudo dpkg -i python-construct_2.5.2-1_all.deb
```

### dfVFS
The dfVFS build instructions can be found [here](https://github.com/log2timeline/dfvfs/wiki/Building). Note that for dfVFS to function correctly several dependencies, like pytsk, mentioned later in a section of this page, are required.

Download the latest source package from: https://github.com/log2timeline/dfvfs/releases

To build deb files run the following command from the build root directory:
```
tar xvf dfvfs-20140219.tar.gz 
cd dfvfs-20140219/
cp -rf dpkg debian
dpkg-buildpackage -rfakeroot
cd ...
```

This will create the following files in the build root directory:
```
python-dfvfs_20140219-1_all.deb
```

To install the required deb files run:
```
sudo dpkg -i python-dfvfs_20140219-1_all.deb
```

### DPKT
**Note that Unbuntu 14.04 provides DPKT 1.6 which contains known issues hence we recommend upgrading to version 1.8.**

**TODO describe**

### Hachoir
To install hachoir run:
```
sudo apt-get install python-hachoir-core python-hachoir-metadata python-hachoir-parser
```

### IPython
To install IPython run:
```
sudo apt-get install ipython
```

For information on how to build IPython from source see: http://ipython.org/ipython-doc/stable/install/install.html

### Libprotobuf and Python-bindings
To install libprotobuf and Python-bindings run:
```
sudo apt-get install libprotobuf7 python-protobuf
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
```
sudo apt-get install zlib1g-dev bzip2-dev libssl-dev libfuse-dev
```

Since the build process for the libyal libraries is very similar, the following paragraph provides building libevt as an example. For more details see the build instructions of the individual projects e.g. https://github.com/libyal/libevt/wiki/Building.

Note that there is also a script to batch build the libyal dependencies more information here: https://code.google.com/p/libyal/wiki/LibyalBuild

#### Example: libevt and Python-bindings
Download the latest source package from: https://github.com/libyal/libevt/releases

To build deb files run the following command from the build root directory:
```
tar xfv libevt-alpha-20150105.tar.gz
cd libevt-20130923
cp -rf dpkg debian
dpkg-buildpackage -rfakeroot
cd ..
```

This will create the following files in the build root directory:
```
libevt_20150105-1_amd64.deb
libevt-dbg_20150105-1_amd64.deb
libevt-dev_20150105-1_amd64.deb
libevt-python_20150105-1_amd64.deb
libevt-python-dbg_20150105-1_amd64.deb
libevt-tools_20150105-1_amd64.deb
```

To install the required deb files run:
```
sudo dpkg -i libevt_20150105-1_amd64.deb libevt-python_20150105-1_amd64.deb
```

### Libyaml and Python-bindings
To install libyaml and Python-bindings run:
```
sudo apt-get install libyaml-0-2 python-yaml
```

### psutil
To install psutil run:
```
sudo apt-get install python-psutil
```

### PyParsing
**Note that Unbuntu 14.04 provides python-pyparsing 2.0.1 which contains known issues hence we recommend upgrading to version 2.0.2.**

**TODO: should this be version 2.0.3?**

Download the 2.0.2 version from http://sourceforge.net/projects/pyparsing/files/pyparsing/pyparsing-2.0.2/ and the [Debian packaging files](https://googledrive.com/host/0B30H7z4S52FleW5vUHBnblJfcjg/3rd%20party/build-files/deprecated/python-pyparsing-2.0.2-dpkg.tar.gz).

To build deb files run the following command from the build root directory:
```
tar zxfv pyparsing-2.0.2.tar.gz
cd pyparsing-2.0.2/
tar zxfv ../python-pyparsing-2.0.2-dpkg.tar.gz
cp -rf dpkg debian
dpkg-buildpackage -rfakeroot
cd ..
```

This will create the following files in the build root directory:
```
python-pyparsing-2.0.2-1_all.deb
```

To install the required deb files run:
```
sudo dpkg -i python-pyparsing-2.0.2-1_all.deb
```

### PySQLite
Install the following dependencies for building PySQLite:
```
sudo apt-get install libsqlite3-dev
```

**TODO describe**

### pytz
To install pytz run:
```
sudo apt-get install python-tz
```

### Sleuthkit and Pytsk
The build and install Sleuthkit and Pytsk see:

* https://github.com/py4n6/pytsk/wiki/Building-SleuthKit
* https://github.com/py4n6/pytsk/wiki/Building