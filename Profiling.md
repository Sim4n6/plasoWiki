## Profiling memory usage
The memory usage of the worker processes used by log2timeline.py can be profiled with guppy.

### Profiling with guppy
To enable profiling you'll need to install [guppy](https://pypi.python.org/pypi/guppy), version 0.1.10 or later is recommended.

If plaso detects that guppy is available it will enable the profiling options, e.g.
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

## Profiling parsers
To profile the CPU usage of the parsers run log2timeline.py with the following options:
```
log2timeline.py --profile --profiling-type=parsers plaso.db image.raw
```