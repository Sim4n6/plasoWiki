## log2timeline failing dependencies check

When I run log2timeline it warns that certain dependencies are missing e.g.
```
Checking availability and versions of plaso dependencies.
[FAILURE]       missing: pyewf.
```

**TODO: add more text**

# Mac OS-X 

See: [Troubleshooting Mac OS X
](https://github.com/log2timeline/plaso/wiki/Troubleshooting-Mac-OS-X)

## On Windows Plaso keeps telling me SQLite3 is too old

The Python installation bundles its own version of SQLite3 that is older than the version required by Plaso. Fix this by

* Removing the old version of SQLite3:
```
C:\Python27\DLL\sqlite3.dll
C:\Python27\DLL\_sqlite3.pyd
C:\Python27\Lib\sqlite3\
```
* Installing a newer version of SQLite3, if not already installed.

Also see: https://github.com/log2timeline/plaso/wiki/Dependencies-Windows#pysqlite
