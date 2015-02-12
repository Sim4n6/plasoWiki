This page contains detailed instructions on how to build and install dependencies on Windows.

## Manual build
### Build essentials
Make sure the necessary building tools and development packages are installed on the system:

* [Python 2.7 Windows installation](http://python.org/download/)
* [Python setup tools](http://pypi.python.org/pypi/setuptools/)
* Microsoft Visual Studio 2008 or later

**Note that plaso itself is platform independent but if you use a 64-bit version of Python all of the dependencies should be compiled as 64-bit.**

To build plaso with Microsoft Visual Studio you'll need to install Microsoft Visual Studio 2008 (or later). The express version is sufficient. Note that if you want to build a 64-bit version with the express version you'll need at least 2010.

First create a build root directory:
```
C:\plaso-build\
```
