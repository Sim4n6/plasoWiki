Plaso supports various profiling options for troubleshooting and performance tuning.

## Profiling CPU usage
### Profiling parsers
To profile the CPU usage of the parsers run log2timeline.py with the following options:
```
log2timeline.py --profile --profiling-type=parsers plaso.db image.raw
```

### Profiling serialization
**TODO**

### Profiling storage
**TODO**

## Profiling memory usage
The memory usage of the worker processes used by log2timeline.py can be profiled with guppy.

### Profiling with guppy
To enable profiling you'll need to install [guppy](https://pypi.python.org/pypi/guppy), version 0.1.10 or later is recommended.

If plaso detects that guppy is available it will enable the memory profiling option. To profile the memory usage of the parsers and workers run log2timeline.py with the following options:
```
log2timeline.py --profile --profiling-sample-rate=5000 --profiling-type=memory plaso.dump image.raw
```

This will create a #.hpy file per worker, where # is the number of the worker.

Guppy has a built-in profile browser to view the .hpy files e.g.
```
from guppy import hpy
heapy = hpy()
heapy.pb('0.hpy')
```