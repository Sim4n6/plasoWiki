**TODO: migrating from https://sites.google.com/a/kiddaland.net/plaso/developer/troubleshooting**

This page contains instructions that can be used to assist you in debugging potential issues with the plaso and its dependencies.

## Quick list

1. Check the [commit history](https://github.com/log2timeline/plaso/commits/master) and [issue tracker](https://github.com/log2timeline/plaso/issues?q=is%3Aissue) if the bug has already been fixed;
2. If you are running the development release make sure plaso and dependencies are up to date, see: [Developers Guide](https://github.com/log2timeline/plaso/wiki/Developers-Guide)
3. Try to isolate the error, see below.

If everything fails create a new issue on the [issue tracker](https://github.com/log2timeline/plaso/issues). Please provide as much detailed information as possible, keep in mind that:

* we cannot fix errors based on vague descriptions;
* we cannot look into your thoughts or on your systems;
* we cannot easily isolate errors if you keep changing your test environment.


Hence please provide us with the following details:

* What steps will reproduce the problem? What output did you expect? What do you see instead?
* What version of plaso/log2timeline are you using? (use log2timeline.py -v to see)
* On what operating system and architecture? (be specific, as in Mac OS X Mountain Lion, 10.8.2 for instance or 64-bit Windows 7)
* Are you processing a storage media image, if so which format, a directory or on an individual file?
* Were you able to isolate the error to a specific file? Is it possible to share the file with the developer?
* Any additional information that could be of use e.g. build logs, error logs, debug logs, etc.

**Note that the github issue tracker uses [markdown](https://help.github.com/articles/markdown-basics/)**

Also see the sections below on how to troubleshoot issues of a specific nature.

## Isolating errors
The most important part of troubleshooting is isolating the error.

If an error occurs when processing a storage media image try to run with the storage image media file and/or the file system directly mounted. Mounting the storage image media file will bypass libraries (modules) supporting the storage image media format.

If the high memory usage still persists try mounting the file system as well to bypass bypass libraries (modules) supporting the file system, e.g. the SleuthKit and pytsk.

Also try running in single process mode this will bypass any issues with multi processing.

## Crashes, hangs and tracebacks
In the context of plaso crashes and tracebacks have different meanings:

* crash; an error in compiled code, often causes an abrupt termination of the program you were running
* traceback; an error in Python code, can cause an abrupt termination of the program you were running but not necessarily

### Analyzing crashes with gdb
Once you've isolated the file that causes the crash and you cannot share the file you can generate a back trace that can help us fix the error.

First make sure you have the debug symbols installed.

Then run the plaso as a single process with gdb:
```
gdb --ex r --args log2timeline.py --single-process -d /tmp/test.dump /tmp/file_that_crashes_the_tool
```

To generate a back trace:
```
bt
```

Note that often the first 10 lines of the back trace are sufficient information.

An alternative approach is to attach a debugger to it once the program is running:
```
gdb -p PID
```

Continue running
```
c
```

Wait until the crash occurs and generate a back trace.

## High memory usage
Plaso consists of various components. It can happen that one of these components uses a lot of memory or even leaks memory. In these cases it is important to isolate the error, see before, to track down what the possible culprit is.

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