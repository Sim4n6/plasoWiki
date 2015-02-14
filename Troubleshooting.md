**TODO: migrating from https://sites.google.com/a/kiddaland.net/plaso/developer/troubleshooting**

This page contains instructions that can be used to assist you in debugging potential issues with the plaso and its dependencies.

## Quick list

1. Check the [commit history](https://github.com/log2timeline/plaso/commits/master) and [issue tracker](https://github.com/log2timeline/plaso/issues?q=is%3Aissue) if the bug has already been fixed;
2. If you are running the development release make sure plaso and dependencies are up to date, see: [Developers Guide](https://github.com/log2timeline/plaso/wiki/Developers-Guide)

If everything fails create a new issue on the [issue tracker](https://github.com/log2timeline/plaso/issues). Please provide as much detailed information as possible. See the sections below on how to troubleshoot issues of a specific nature.

**Note that the github issue tracker uses [markdown](https://help.github.com/articles/markdown-basics/)**

## High memory usage
Plaso consists of various components. It can happen that one of these components uses a lot of memory or even leaks memory. In these cases it is important to narrow it down what possible culprit is.

If the issue occurs when processing a storage media image try to run with the storage image media file and/or the file system directly mounted. Mounting the storage image media file will bypass libraries (modules) supporting the storage image media format.

If the high memory usage still persists try mounting the file system as well to bypass bypass libraries (modules) supporting the file system, e.g. the SleuthKit and pytsk.

Also try running in single process mode this will bypass any issues with multi processing.

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

* [Troubleshooting Windows specific issues](https://github.com/log2timeline/plaso/wiki/Troubleshooting-Windows)
* [Troubleshooting Plaso Issues - Memory Edition](http://blog.kiddaland.net/2014/11/troubleshooting-plaso-issues-memory.html)