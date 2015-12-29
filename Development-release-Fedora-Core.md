To download the latest version of Plaso you'll need to install the git tools:
```
sudo yum install git
```

Checkout the plaso source from the git repo:
```
git clone https://github.com/log2timeline/plaso.git
```

To be able to run the plaso [development release](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap) on Fedora Core or equivalent you'll have to have installed the [dependencies](https://github.com/log2timeline/plaso/wiki/Dependencies-Fedora-Core).

Check if you have all the dependencies installed and have the right minimum version:
```
python utils/check_dependencies.py
```

**Note that some dependencies are actively under development and can be frequently updated, therefore we recommend checking the status of the dependencies regularly.**

## Development tools
If you intend to do development on plaso you'll also need to install some development tools:

* PyLint
* Python Mock

### PyLint
At the moment Plaso development requires PyLint 1.4.x.

```
sudo yum install pylint
```

**TODO: check distributed version**

For pylint 1.5.x the following additional dependencies are required:
* https://pypi.python.org/pypi/lazy-object-proxy
* https://pypi.python.org/pypi/wrapt

### Python Mock
**TODO: add description.**
