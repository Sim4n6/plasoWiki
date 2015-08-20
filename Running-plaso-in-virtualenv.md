**TODO: add more text**

# Setting up virtualenv
To install virtualenv on Ubuntu (or equivalent) run:
```
sudo apt-get install python-virtualenv
```

# Setting up plaso 1.2 in virtualenv
To create a virtualenv:
```
virtualenv plaso-1.2
```

To activate the virtualenv:
```
source ./plaso-1.2/bin/activate
```

To install Python modules from source:
```
./plaso-1.2/bin/python setup.py build
./plaso-1.2/bin/python setup.py install
```