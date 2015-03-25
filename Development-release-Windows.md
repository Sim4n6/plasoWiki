To download the latest version of Plaso you'll need to install the git tools: http://git-scm.com/downloads

Checkout the plaso source from the git repo:
```
git clone https://github.com/log2timeline/plaso.git
```

**If you intend to submit code make sure to configure git to use convert to the Unix-style end-of-line characters (linefeed) on submission and not have the Windows-style end-of-line characters (carriage return + linefeed).** 

We recommend to configure your editor of choice to use linefeed only and turn off git's autocrlf:
```
git config --global core.autocrlf false
```

To be able to run the plaso [development release](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap) on Windows you'll have to have installed the [dependencies](https://github.com/log2timeline/plaso/wiki/Dependencies-Windows).

Check if you have all the dependencies installed and have the right minimum version:
```
C:\Python27\python.exe utils\check_dependencies.py
```

**Note that some dependencies are actively under development and can be frequently updated, therefore we recommend checking the status of the dependencies regularly.**

## Running the development release
To run the development release directly from source make sure Python can find the plaso source files by setting PYTHONPATH correspondingly.
```
set PYTHONPATH=C:\plaso-build\plaso
```

To run e.g. pinfo:
```
C:\Python27\python.exe C:\plaso-build\plaso\plaso\frontend\pinfo.py plaso.db
```

## Development tools
If you intend to do development on plaso you'll also need to install some development tools:

* PyLint
* Python Mock

### PyLint
We recommend PyLint 1.0.0 or later.

**TODO: add description.**

### Python Mock
Download the latest source package from: https://pypi.python.org/pypi/mock

To build the MSI file run the following commands from the build root directory:
```
tar xvf mock-1.0.1.tar.gz
cd mock-1.0.1\
C:\Python27\python.exe setup.py bdist_msi
cd ..
```

This will create a MSI in the dist sub directory e.g.:
```
dist\mock-1.0.1.win32.msi
```

Install the MSI.

## Creating a packaged release
To create a Windows packaged release from the development release you also need:

* PyInstaller

### PyInstaller
Download the latest source from:
```
git clone -b master git://github.com/pyinstaller/pyinstaller.git
```

**Note that setup.py build and install is currently disabled, so we need to run PyInstaller from its download directory.**

#### Rebuilding the PyInstaller bootloader
By default PyInstaller is code compatible with Windows XP SP2 (5.1). If you need to support a Windows version earlier you'll need to recompile the PyInstaller "bootloader" with Visual Studio 2008. Note that Visual Studio 2010 is not compatible with Windows 2000.

cd PyInstaller\bootloader
C:\Python27\python.exe waf configure build install

#### Microsoft Visual C++ 2010 Redistributable Package
If you're building with Visual Studio note that for some reason PyInstaller does not include the Microsoft Visual C++ 2010 run-time DLLs you can find them here:

* [Microsoft Visual C++ 2010 Redistributable Package (x86)](http://www.microsoft.com/en-us/download/details.aspx?id=5555)
* [Microsoft Visual C++ 2010 Redistributable Package (x64)](http://www.microsoft.com/en-us/download/details.aspx?id=14632)

### Preparations
If you are intending to distribute the packaged release make sure to do the following steps:

`1`. Remove code that cannot be redistributed due to a license restriction, by running:
```
sh utils/prep_dist.sh
```

**Note that you'll need to run this under Cygwin or equivalent.**

`2`. Distribute a copy of:
```
AUTHORS
ACKNOWLEDGEMENT
LICENSE
config\licenses\*
```

### Packaging
First check if the PyInstaller build script: config\windows\make.bat is configured correctly for your build environment.

From the plaso source directory run the following commands:

To build plaso with PyInstaller run:
```
config\windows\make.bat
```

This will create sub directories for each of the tools under dist.

To merge all the sub directories into one run:
```
config\windows\make_dist.bat
```

This will create: dist\plaso

To do a very rudimentary test to see if the packaged binaries work run:
```
config\windows\make_check.bat
```

And finally create a zip archive of: dist\plaso
