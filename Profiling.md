Plaso supports various profiling options for troubleshooting and performance tuning.

## Profiling CPU usage
### Profiling parsers
To profile the CPU usage of the parsers run log2timeline.py with the following options:
```
log2timeline.py --profile --profiling-type=parsers plaso.db image.raw
```

### Profiling serialization
To profile the CPU usage of the serialization run log2timeline.py with the following options:
```
log2timeline.py --profile --profiling-type=serializers plaso.db image.raw
```

**TODO: add serialization profiling to psort as well**

### Profiling storage
**TODO: add write profiling for storage?**

## Profiling memory usage
The memory usage of the worker processes used by log2timeline.py can be profiled with guppy.

### Profiling Python memory usage with guppy
To profile Python memory usage with guppy you'll need to install [guppy](https://pypi.python.org/pypi/guppy), version 0.1.10 or later is recommended. If plaso detects that guppy is available it will enable the `guppy` profiling option.

Run log2timeline.py with the following options:
```
log2timeline.py --profilers=guppy --profiling_directory=profile --profiling-sample-rate=5000 plaso.dump image.raw
```

This will create a #.hpy file per worker, where # is the number of the worker.

Guppy has a built-in profile browser to view the .hpy files e.g.
```
from guppy import hpy
heapy = hpy()
heapy.pb('0.hpy')
```