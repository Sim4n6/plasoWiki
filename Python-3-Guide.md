## Python 3 Guide
At the moment plaso is not Python 3 compatible. This page contains information about which Python language features to use to help plaso to stay Python 2.7 compatible and become Python 3 compatible.

### Python
See: https://docs.python.org/3/howto/pyporting.html

* the result of \ is a floating point, use divmod() instead (or \\)
* exception.message no longer accessible
* % format notation on longer supported, replaced by format and {} notation
* explicitly mark byte strings (b'')
* dict.sort() no longer works
* str is Unicode not bytes so str.decode fails
* more picky about string conversion in format e.g. printing a set as {0:s}
* Use `__unicode__` in preference of `__str__`
* unicode() no longer works
* open() must be passed binary mode
* next() replaced by `__next__()`
* dict iter functions: https://docs.python.org/3.1/whatsnew/3.0.html#views-and-iterators-instead-of-lists

from __future__ import unicode_literals

#### print
In Python 3 print is a function:
```
print "Test" => print("Test")
```

For compatibility with Python 2, and to stop pylint complaining, add the following import:
```
from __future__ import print_function
```

#### StringIO.StringIO
StringIO.StringIO is replaced by io.StringIO and io.BytesIO

#### xrange()
xrange() is no longer supported by Python 3 use range() instead:
```
xrange(10) => range(0, 10)
```

### C extensions
See: http://python3porting.com/cextensions.html

### Python 3 status
Dependency | Python 3 compatible
--- | ---
artifacts | yes
bencode | unknown
binplist | unknown
construct | unknown (version 3?) 
dateutil.parser | unknown
pefile | no
dpkt | unknown
hachoir_core | unknown
hachoir_parser | unknown
hachoir_metadata | unknown
IPython | yes
pefile | no
protobuf | yes (as of 2.6.0)
psutil | yes
pybde | yes (as of 20141222)
pyesedb | yes (as of 20141224)
pyevt | yes (as of 20141220)
pyevtx | yes (as of 20141220)
pyewf | yes (as of 20141225)
pyfwsi | yes (as of 20141223)
pylnk | yes (as of 20141220)
pymsiecf | yes (as of 20141222)
pyolecf | yes (as of 20141221)
pyparsing | yes
pyqcow | yes (as of 20141221)
pyregf | yes (as of 20141222)
pysmdev | yes (as of 20141225)
pysmraw | yes (as of 20141221)
pytsk | yes (as of 20141224)
pytz | yes
pyvhdi | yes (as of 20141221)
pyvmdk | yes (as of 20141221)
pyvshadow | yes (as of 20141223)
six | yes
sqlite3 (pysqlite) | unknown
yaml | yes