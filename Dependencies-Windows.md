**TODO: work in progress migrating from: https://sites.google.com/a/kiddaland.net/plaso/developer/building-the-tool/windows**

This page contains detailed instructions on how to build and install dependencies on Windows.

There are multiple ways to install the dependencies on Windows:

* Using the [log2timeline devtools](https://github.com/log2timeline/devtools) to batch build most of the dependencies;
* Manual build of the dependencies.

## Batch build
**TODO describe**

## Manual build
For ease of maintenance the following instructions use as much MSI package files as possible via "Programs and Features". Note that the resulting MSI files are not intended for public redistribution.

**Note that when making MSI packages, make sure the remove the previous versions before installing the newer version.**

Alternative installation methods like installing directly from source, using easy_install or pip are not recommended because when not maintained correctly they can mess up your setup more easily than using MSIs. E.g. easy_installer and pip do not always remove older versions, e.g. when upgrading IPython 0.13 to 1.1. though Python distutil generated MSI packages don't detect and remove previous versions either it is less likely you'll end up with multiple different versions of the same package installed side-by-side.

If you run into problems building, installing or running the dependencies first check: [Troubleshooting](https://github.com/log2timeline/plaso/wiki/Troubleshooting-Windows).

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

If you are not familiar with extracting tar files on Windows see: [How to unpack a tar file in Windows](https://wiki.haskell.org/How_to_unpack_a_tar_file_in_Windows)

### Bencode
Download the latest source package from: https://pypi.python.org/pypi/bencode

To build the MSI file run the following commands from the build root directory:
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
Download the latest source package from: https://code.google.com/p/binplist/downloads/list

To build the MSI file run the following commands from the build root directory:
```
tar xvf binplist-0.1.4.tar.gz
cd binplist-0.1.4\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\binplist-0.1.4.win32.msi
```

Install the MSI.

### Construct
Construct is dependent on six see the instructions below how to build and install six.

Download the latest 2.x source package from: https://pypi.python.org/pypi/construct#downloads

To build the MSI file run the following commands from the build root directory:
```
tar xfv construct-2.5.2.tar.gz
cd construct-2.5.2\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\construct-2.5.2.win32.msi
```

Install the MSI.

### dfVFS
The dfVFS build instructions can be found [here](https://github.com/log2timeline/dfvfs/wiki/Building). Note that for dfVFS to function correctly several dependencies, like pytsk, mentioned later in a section of this page, are required.

Download the latest source package from: https://github.com/log2timeline/dfvfs/releases

To build the MSI file run the following commands from the build root directory:
```
tar xfv dfvfs-20150129.tar.gz
cd dfvfs\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\dfvfs-20150129.win32.msi
```

Install the MSI.

### DPKT
Download the latest source package from: https://code.google.com/p/dpkt/downloads/list

To build the MSI file run the following commands from the build root directory:
```
tar xfv dpkt-1.8.tar.gz
cd dpkt\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\dpkt-1.8.win32.msi
```

Install the MSI.

### Hachoir
Download the latest source package from: https://bitbucket.org/haypo/hachoir/wiki/Install/source

You'll need:

* hachoir-core-1.3.3.tar.gz
* hachoir-parser-1.3.4.tar.gz
* hachoir-metadata-1.3.3.tar.gz

To build the MSI files run the following commands from the build root directory:

```
tar xfv hachoir-core-1.3.3.tar.gz
cd hachoir-core-1.3.3\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

```
tar xfv hachoir-parser-1.3.4.tar.gz
cd hachoir-parser-1.3.4\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

```
cd C:\plaso-build\hachoir-metadata-1.3.3\
C:\Python27\python.exe setup.py build
C:\Python27\python.exe setup.py install
### Libyaml and Python-bindings
Download the latest source package from: http://pyyaml.org/wiki/PyYAML

```
tar xfv PyYAML-3.11.tar.gz
cd PyYAML-3.10\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\PyYAML-3.10.win32.msi
```

Install the MSI.

### Psutils
Download the latest source package from: https://pypi.python.org/pypi/psutil

To build the MSI file run the following commands from the build root directory:
```
tar xfv psutil-2.2.1.tar.gz
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\psutil-2.2.1.win32-py2.7.msi
```

Install the MSI.

To build psutil with Visual Studio 2010 we need to run the previous commands from either the "Visual Studio Command Prompt (2010)" or "Windows SDK 7.1 Command Prompt" (or equivalent). Check if the VS100COMNTOOLS environment variable is set:
```
echo %VS100COMNTOOLS%
```

Then set the VS90COMNTOOLS to match VS100COMNTOOLS for setup.py to detect Visual Studio 2010 correctly:
```
set VS90COMNTOOLS=%VS100COMNTOOLS%
```

### PyParsing
Download the latest source package from: http://sourceforge.net/projects/pyparsing/files/

```
tar xfv pyparsing-2.0.3.tar.gz
cd pyparsing-2.0.3\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\pyparsing-2.0.3.win32.msi
```

Install the MSI.

### Six
Download the latest 1.x source package from: https://pypi.python.org/pypi/six#downloads

To build the MSI file run the following commands from the build root directory:
```
tar xfv six-1.9.0.tar.gz
cd C:\plaso-build\six-1.9.0\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\six-1.9.0.win32.msi
```

Install the MSI.