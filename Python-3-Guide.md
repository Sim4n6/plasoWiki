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