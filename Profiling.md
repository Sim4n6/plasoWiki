## Profiling memory usage

### Profiling with guppy
Plaso supports memory profiling of the worker processes. To enable profiling you'll need to install guppy, version 0.1.10 or later is recommended.

If plaso detects that guppy is available it will enable the profiling options, e.g.
```
log2timeline.py --profile --profile-sample-rate=5000 plaso.db image.raw
```

This will create a #.hpy file per worker, where # is the number of the worker.

Guppy has a built-in profile browser to view the .hpy files e.g.
```
from guppy import hpy
heapy = hpy()
heapy.pb('0.hpy')
```

## Also see

* [Troubleshooting Plaso Issues - Memory Edition](http://blog.kiddaland.net/2014/11/troubleshooting-plaso-issues-memory.html)