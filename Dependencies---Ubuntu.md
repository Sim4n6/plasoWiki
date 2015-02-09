This page contains detailed instructions on how to build and install dependencies on Ubuntu.

**Note that the instructions in this page assume you are running on Ubuntu 14.04.**

## Prepackaged dependencies
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