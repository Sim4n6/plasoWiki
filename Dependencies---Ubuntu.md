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
sudo apt-get install libbde-dbg libbde-python-dbg
```

**TODO complete list of dependencies.**

## Batch build
**TODO describe**

## Manual build
It is impossible for us to support all flavors of Ubuntu out there, so if you want smooth sailing, we recommend sticking with the supported version or live with the fact that a manual build of the dependencies can be a tedious task.

For ease of maintenance the following instructions use as much deb package files as possible. Note that the resulting deb files are not intended for public redistribution.

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
**TODO describe**

### binplist
Download the source package from: https://code.google.com/p/binplist/downloads/list

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

To install the deb files run:
```
sudo dpkg -i binplist_0.1.4-1_all.deb
```

### Construct
Note that Unbuntu 14.04 ships with construct 2.5.1 which contains known issues hence we recommend upgrading to version 2.5.2.

**TODO describe**

**TODO migrate the rest of the documentation**

### libyal
Install the following dependencies for building libyal:
```
sudo apt-get install libfuse-dev
```

**TODO**