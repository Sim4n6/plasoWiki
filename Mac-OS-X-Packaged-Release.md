To install the Mac OS X Packaged Release of plaso you need to download the latest version from http://download.log2timeline.net

Find the highest version number (as of this time version 1.4.0) and inside the folder called ```release``` is a DMG file.

The DMG file can be either opened by double clicking it or by using the command line.

```
hdiutil attach plaso-1.4.0_macosx-10.11.dmg
```

The terminal has to be used to install the tool itself.

```
cd /Volumes/plaso-1.4.0
sudo ./install.sh
```

Then the DMG can be unmounted either via the GUI or the command line:
```
hdiutil detach /Volumes/plaso-1.4.0
```

## Mac OS X 10.11 (El Capitan)
Note that Mac OS X 10.11 (El Capitan) comes with pyparsing 2.0.1 and disallows removing these files by default. To be able to remove the files you'll have to disable System Integrity Protection (SIP or rootless), which is not recommended since some system scripts can depend on this version of pyparsing.

Alternatively you can override PYTHONPATH e.g.:
```
PYTHONPATH=/Library/Python/2.7/site-packages/ log2timeline.py
```

Which you can alias e.g.
```
alias log2timeline.py="PYTHONPATH=/Library/Python/2.7/site-packages/ log2timeline.py"
```

Or use the shell script helpers provided in the DMG e.g.
```
log2timeline.sh
```
