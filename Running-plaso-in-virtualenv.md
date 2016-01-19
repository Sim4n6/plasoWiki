**TODO: add more text**

# Setting up plaso in virtualenv
## Fedora Core
### Install virtualenv
To install virtualenv on Fedora Core (or equivalent) run:
```
sudo dnf install python-virtualenv
```

### Installing build dependencies
**TODO add more text**

## Ubuntu
### Installing virtualenv
To install virtualenv on Ubuntu (or equivalent) run:
```
sudo apt-get install python-virtualenv
```

### Installing build dependencies
**TODO add more text**
```
sudo apt-get install libyaml-dev
```

## Setting up plaso in virtualenv
To create a virtualenv:
```
virtualenv plasoenv
```

To activate the virtualenv:
```
source ./plasoenv/bin/activate
```

**Note that using pip outside virtualenv is not recommended since it ignores your systems package manager.**

```
pip install --upgrade pip
```

```
pip install PyYAML artifacts
```

Seeing pip wants versions to be [PEP-426](https://www.python.org/dev/peps/pep-0426/) compliant and libyal uses a different numbering schema the `--pre` option needs to be passed to pip to install libyal Python-bindings:
```
pip install --pre libbde-python libesedb-python libevt-python libevtx-python libfsntfs-python libfwsi-python liblnk-python libmsiecf-python libolecf-python libqcow-python libregf-python libsigscan-python libsmdev-python libsmraw-python libvhdi-python libvmdk-python libvshadow-python libvslvm-python
```

To install Python modules from source:
```
VENVDIR=`readlink -f plasoenv`
${VENVDIR}/bin/python setup.py build
${VENVDIR}/bin/python setup.py install
```

To deactivate the virtualenv run:
```
deactivate
```
