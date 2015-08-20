**TODO: add more text**

# Setting up virtualenv
To install virtualenv on Ubuntu (or equivalent) run:
```
sudo apt-get install python-virtualenv
```

# Setting up plaso 1.2 in virtualenv
```
sudo apt-get install libyaml-dev
```

To create a virtualenv:
```
virtualenv plaso-1.2
```

To activate the virtualenv:
```
VENVDIR=`readlink -f plaso-1.2`
source ${VENVDIR}/bin/activate
```

```
pip install PyYAML artifacts
```

```
pip install --pre pymsiecf
```

To install Python modules from source:
```
${VENVDIR}/bin/python setup.py build
${VENVDIR}/bin/python setup.py install
```