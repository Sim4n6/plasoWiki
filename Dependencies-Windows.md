This page contains detailed instructions on how to build and install dependencies on Windows.

## Manual build
For ease of maintenance the following instructions use as much MSI package files as possible via "Programs and Features". Note that the resulting MSI files are not intended for public redistribution.

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

If you are not familiar with extracting a tar on Windows see: [How to unpack a tar file in Windows](https://wiki.haskell.org/How_to_unpack_a_tar_file_in_Windows)

### Bencode
Download the latest source package from: https://pypi.python.org/pypi/bencode

To build the MSI file run the following command from the build root directory:
```
tar xvf bencode-1.0.tar.gz
cd bencode-1.0\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\bencode-1.0.win32.msi
```

Install the MSI.

### Binplist
Download the latest source package from: https://code.google.com/p/binplist

To build the MSI file run the following command from the build root directory:
```
tar xvf binplist-0.1.4.tra.gz
cd binplist-0.1.4\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\binplist-0.1.4.win32.msi
```

Install the MSI.
