### Python 3 Guide
At the moment plaso is not Python 3 compatible. This page contains information about which Python language features to use to help plaso to stay Python 2.7 compatible and become Python 3 compatible.

#### xrange()
xrange() is no longer supported by Python 3 use range() instead:
```
xrange(10) => range(0, 10)
```

### Python 3 status
Dependency | Python 3 compatible
--- | ---
artifacts | <span style="color:green">yes</span>
bencode | unknown
binplist | unknown
construct | unknown (version 3?) 
dateutil.parser | unknown
pefile | <span style="color:red">no</span>
dpkt | unknown
hachoir_core | unknown
hachoir_parser | unknown
hachoir_metadata | unknown
IPython | <span style="color:green">yes</span>
pefile | <span style="color:red">no</span>
protobuf | <span style="color:green">yes (as of 2.6.0)</span>
psutil | <span style="color:green">yes</span>
pybde | <span style="color:green">yes (as of 20141222)</span>
pyesedb | <span style="color:green">yes (as of 20141224)</span>
pyevt | <span style="color:green">yes (as of 20141220)</span>
pyevtx | <span style="color:green">yes (as of 20141220)</span>
pyewf | <span style="color:green">yes (as of 20141225)</span>
pyfwsi | <span style="color:green">yes (as of 20141223)</span>
pylnk | <span style="color:green">yes (as of 20141220)</span>
pymsiecf | <span style="color:green">yes (as of 20141222)</span>
pyolecf | <span style="color:green">yes (as of 20141221)</span>
pyparsing | <span style="color:green">yes</span>
pyqcow | <span style="color:green">yes (as of 20141221)</span>
pyregf | <span style="color:green">yes (as of 20141222)</span>
pysmdev | <span style="color:green">yes (as of 20141225)</span>
pysmraw | <span style="color:green">yes (as of 20141221)</span>
pytsk | <span style="color:green">yes (as of 20141224)</span>
pytz | <span style="color:green">yes</span>
pyvhdi | <span style="color:green">yes (as of 20141221)</span>
pyvmdk | <span style="color:green">yes (as of 20141221)</span>
pyvshadow | <span style="color:green">yes (as of 20141223)</span>
six | <span style="color:green">yes</span>
sqlite3 (pysqlite) | unknown
yaml | <span style="color:green">yes</span>
