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
virtualenv plaso-venv
```

To activate the virtualenv:
```
source ./plaso-venv/bin/activate
```

**Note that using pip outside virtualenv is not recommended since it ignores your systems package manager.**

```
pip install PyYAML artifacts
```

Seeing pip wants versions to be [PEP-426](https://www.python.org/dev/peps/pep-0426/) compliant the `--pre` option needs to be passed to pip to install them:
```
pip install --pre pyevt pyevtx pymsiecf pysigscan
```

To install Python modules from source:
```
VENVDIR=`readlink -f plaso-venv`
${VENVDIR}/bin/python setup.py build
${VENVDIR}/bin/python setup.py install
```

To deactivate the virtualenv run:
```
deactivate
```