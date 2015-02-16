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

Alternative installation methods like installing directly from source, using easy_install or pip are not recommended because when not maintained correctly they can mess up your setup more easily than using MSIs. E.g. easy_installer and pip do not always remove older versions, e.g. when upgrading IPython 0.13 to 1.1, though Python distutil generated MSI packages don't detect and remove previous versions either it is less likely you'll end up with multiple different versions of the same package installed side-by-side.

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

### IPython
**Note the MSI packaging for IPython seems to be broken! E.g. the files in scripts/ directory are missing .py extensions.**

Download the latest 1.x source package from: https://github.com/ipython/ipython/releases

To build the MSI file run the following commands from the build root directory:
```
tar xfv ipython-1.2.1.tra.gz
cd ipython-1.2.1\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\ipython-1.2.1.win32.msi
```

Install the MSI.

For information on how to build IPython from source see: http://ipython.org/ipython-doc/stable/install/install.html

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

This will create a MSI in the dist sub directory e.g.:
```
dist\hachoir-core-1.3.3.win32.msi
```

Install the MSI.

```
tar xfv hachoir-parser-1.3.4.tar.gz
cd hachoir-parser-1.3.4\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\hachoir-parser-1.3.4.win32.msi
```

Install the MSI.

```
tar xfv hachoir-metadata-1.3.3.tar.gz
cd hachoir-metadata-1.3.3\
C:\Python27\python.exe setup.py bdist_msi
cd ...
```

This will create a MSI in the dist sub directory e.g.:
```
dist\hachoir-metadata-1.3.3.win32.msi
```

Install the MSI.

### Libprotobuf and Python-bindings
Download the latest 2.x source package from: https://github.com/google/protobuf/releases

Extract the source package:
```
tar xfv protobuf-2.5.0.tar.gz
```

To build the proto compiler (protoc) open the Microsoft Visual Studio solution file:
```
protobuf-2.5.0\vsprojects\protobuf.sln
```

Change the solution configuration to "Release".

Build the entire solution or at minimum the protoc project.

For information on how to create a 64-bit build on Visual Studio 2010 express also see the section about [Microsoft Visual Studio 2010 express and 64-bit compilation](https://github.com/log2timeline/plaso/wiki/Dependencies-Windows#microsoft-visual-studio-2010-express-and-64-bit-compilation).

To build the MSI file run the following commands from the build root directory:
```
cd protobuf-2.5.0\python\
C:\Python27\python.exe setup.py bdist_msi
cd ..\..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\protobuf-2.5.0.win32.msi
```

**TODO: check MSI name.**

Install the MSI.

### libyal
The following instructions apply to the following dependencies:

* [libbde](https://github.com/libyal/libbde)
* [libesedb](https://github.com/libyal/libesedb)
* [libevt](https://github.com/libyal/libevt)
* [libevtx](https://github.com/libyal/libevtx)
* [libewf](https://github.com/libyal/libewf)
* [libfwsi](https://github.com/libyal/libfwsi)
* [liblnk](https://github.com/libyal/liblnk)
* [libmsiecf](https://github.com/libyal/libmsiecf)
* [libolecf](https://github.com/libyal/libolecf)
* [libqcow](https://github.com/libyal/libqcow)
* [libregf](https://github.com/libyal/libregf)
* [libsigscan](https://github.com/libyal/libsigscan)
* [libsmdev](https://github.com/libyal/libsmdev)
* [libsmraw](https://github.com/libyal/libsmraw)
* [libvhdi](https://github.com/libyal/libvhdi)
* [libvmdk](https://github.com/libyal/libvmdk)
* [libvshadow](https://github.com/libyal/libvshadow)

Install the following dependencies for building libyal:

* zlib
* bzip2
* dokan

**TODO: describe building dependencies.**

Since the build process for the libyal libraries is very similar, the following paragraph provides building libevt as an example. For more details see the build instructions of the individual projects e.g. https://github.com/libyal/libevt/wiki/Building.

Note that there is also a script to batch build the libyal dependencies more information here: https://code.google.com/p/libyal/wiki/LibyalBuild

#### Example: libevt and Python-bindings
Download the latest source package from: https://github.com/libyal/libevt/releases

Extract the source package:
```
tar xfv libevt-alpha-20131013.tar.gz
```

Open the Microsoft Visual Studio 2008 solution file:
```
C:\plaso-build\libevt-20131013\msvcspp\libevt.sln
```

Build the solution.

For information on how to create a 64-bit build on Visual Studio 2010 express also see the section about [Microsoft Visual Studio 2010 express and 64-bit compilation](https://github.com/log2timeline/plaso/wiki/Dependencies-Windows#microsoft-visual-studio-2010-express-and-64-bit-compilation).

To build the MSI file run the following commands from the build root directory:
```
cd libevt-20131013\pyevt\
C:\Python27\python.exe setup.py bdist_msi
cd ..\..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\pyevt-20131013.1.win32-py2.7.msi
```

Install the MSI.

### Libyaml and Python-bindings
Download the latest source package from: http://pyyaml.org/wiki/PyYAML

To build the MSI file run the following commands from the build root directory:
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

To build the MSI file run the following commands from the build root directory:
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

### Python-dateutil
Download the latest source package from: https://pypi.python.org/pypi/python-dateutil/

To build the MSI file run the following commands from the build root directory:
```
tar xfv python-dateutil-2.4.0.tar.gz
cd python-dateutil-2.4.0\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\python-dateutil-2.4.0.win32.msi
```

Install the MSI.

### pytz
Download the latest source package from: https://pypi.python.org/pypi/pytz

To build the MSI file run the following commands from the build root directory:
```
tar xfv pytz-2014.10.tar.gz
cd pytz-2014.10.tar.gz\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\pytz-2014.10.win32.msi
```

Install the MSI.

### pywin32
Download the latest installer from: http://sourceforge.net/projects/pywin32/files/pywin32/

### Six
Download the latest 1.x source package from: https://pypi.python.org/pypi/six#downloads

To build the MSI file run the following commands from the build root directory:
```
tar xfv six-1.9.0.tar.gz
cd six-1.9.0\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\six-1.9.0.win32.msi
```

Install the MSI.

### Sleuthkit and Pytsk
The build and install Sleuthkit and Pytsk see:

* https://github.com/py4n6/pytsk/wiki/Building-SleuthKit
* https://github.com/py4n6/pytsk/wiki/Building

### Microsoft Visual Studio 2010 express and 64-bit compilation

Enabling 64-bit compilation support on the express version of Microsoft Visual Studio 2010 can be a tedious process. Below are some related links:

* http://msdn.microsoft.com/en-us/library/vstudio/9yb4317s(v=vs.100).aspx
* http://support.microsoft.com/kb/2519277

If you have set it up correctly the following should work:
```
Go to: "Configuration manager -> Active solution platform"
Select "<New>"

Type or select the new platform: "x64"
Copy settings from: "Win32"
Create new project platforms: enabled

For every project "Configuration Properties -> General -> Platform Toolset" = "Windows7.1SDK"
```