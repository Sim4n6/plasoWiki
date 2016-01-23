## log2timeline failing dependencies check

When I run log2timeline it warns that certain dependencies are missing e.g.
```
Checking availability and versions of plaso dependencies.
[FAILURE]       missing: pyewf.
```

**TODO: add more text**

## On Mac OS-X I get strange errors that mention pyparsing

Mac OS-X bundles its own version of pyparsing that is older than the version required by Plaso. Fix this by using the special wrapper scripts (log2timeline**.sh**, et. al.), or if you don't want to do that, manipulate PYTHONPATH so that the newer version is loaded. This is detailed on the Mac OS-X development page: https://github.com/log2timeline/plaso/wiki/Development-release-Mac-OS-X

**TODO: add more text**

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
