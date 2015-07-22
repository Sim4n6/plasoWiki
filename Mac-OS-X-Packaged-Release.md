To install the Mac OS X Packaged Release of plaso you need to download the latest version from http://download.log2timeline.net

Find the highest version number (as of this time version 1.3) and inside the folder called ```release``` is a DMG file.

The DMG file can be either opened by double clicking it or by using the command line.

```
hdiutil attach plaso-1.3.0_macosx-10.10.dmg
```

The terminal has to be used to install the tool itself.

```
cd /Volumes/plaso-1.3.0
sudo ./install.sh
```

Then the DMG can be unmounted either via the GUI or the command line:
```
hdiutil detach /Volumes/plaso-1.3.0
```

