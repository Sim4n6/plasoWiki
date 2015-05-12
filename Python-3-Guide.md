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
artifacts | <font color='green'>yes</font>
bencode | unknown
binplist | unknown
construct | unknown (version 3?) 
dateutil.parser | unknown
pefile | <font color='red'>no</font>
dpkt | unknown
hachoir_core | unknown
hachoir_parser | unknown
hachoir_metadata | unknown
IPython | <font color='green'>yes</font>
pefile | <font color='red'>no</font>
protobuf | <font color='green'>yes (as of 2.6.0)</font>
psutil | <font color='green'>yes</font>
pybde | <font color='green'>yes (as of 20141222)</font>
pyesedb | <font color='green'>yes (as of 20141224)</font>
pyevt | <font color='green'>yes (as of 20141220)</font>
pyevtx | <font color='green'>yes (as of 20141220)</font>
pyewf | <font color='green'>yes (as of 20141225)</font>
pyfwsi | <font color='green'>yes (as of 20141223)</font>
pylnk | <font color='green'>yes (as of 20141220)</font>
pymsiecf | <font color='green'>yes (as of 20141222)</font>
pyolecf | <font color='green'>yes (as of 20141221)</font>
pyparsing | <font color='green'>yes</font>
pyqcow | <font color='green'>yes (as of 20141221)</font>
pyregf | <font color='green'>yes (as of 20141222)</font>
pysmdev | <font color='green'>yes (as of 20141225)</font>
pysmraw | <font color='green'>yes (as of 20141221)</font>
pytsk | <font color='green'>yes (as of 20141224)</font>
pytz | <font color='green'>yes</font>
pyvhdi | <font color='green'>yes (as of 20141221)</font>
pyvmdk | <font color='green'>yes (as of 20141221)</font>
pyvshadow | <font color='green'>yes (as of 20141223)</font>
six | <font color='green'>yes</font>
sqlite3 (pysqlite) | unknown
yaml | <font color='green'>yes</font>
