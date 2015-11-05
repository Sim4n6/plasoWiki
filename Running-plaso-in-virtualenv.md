**TODO: add more text**

# Setting up virtualenv
To install virtualenv on Ubuntu (or equivalent) run:
```
sudo apt-get install python-virtualenv
```

# Setting up plaso in virtualenv
```
sudo apt-get install libyaml-dev
```

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
pip install --pre libevt-python libevtx-python libfwsi-python libfsntfs-python liblnk-python libmsiecf-python libolecf-python libsigscan-python libsmraw-python libvhdi-python libvshadow-python
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