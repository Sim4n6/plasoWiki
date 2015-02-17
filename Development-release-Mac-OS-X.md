To download the latest version of Plaso you'll need to install the git tools: http://git-scm.com/downloads

Checkout the plaso source from the git repo:
```
git clone https://github.com/log2timeline/plaso.git
```

To be able to run the plaso [development release](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap) on Windows you'll have to have installed the [dependencies](https://github.com/log2timeline/plaso/wiki/Dependencies-Mac-OS-X).

Check if you have all the dependencies installed and have the right minimum version:
```
C:\Python27\python.exe utils\check_dependencies.py
```

**Note that some dependencies are actively under development and can be frequently updated, therefore we recommend checking the status of the dependencies regularly.**

## Development tools
If you intend to do development on plaso you'll also need to install some development tools:

* PyLint

### PyLint
**TODO: add description.**