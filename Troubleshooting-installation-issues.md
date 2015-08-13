# Ubuntu

Installing the plaso on Ubuntu should be a breeze if you follow the instructions [here](https://github.com/log2timeline/plaso/wiki/Ubuntu-Packaged-Release), however sometimes there can be conflicting packages installed that cause plaso not to run properly. Most often this is caused by either some unsupported versions of packages being installed or if for some reason some of the dependencies was installed from source at some point and those dependencies are out of date.

If you are having trouble getting plaso to run on your computer after following the installation instructions one of the best first steps is to check if all dependencies are met. One way of doing that is to download the check dependency script and run it.

```
$ wget https://raw.githubusercontent.com/log2timeline/plaso/master/utils/check_dependencies.py
$ python check_dependencies.py
```

The output should be something on these lines:

```
Checking availability and versions of plaso dependencies.
[OK]		artifacts version: 20150409
[OK]		bencode
[OK]		binplist version: 0.1.4
[OK]		construct version: 2.5.2
...
```

An `[ERROR]` status indicates that the version of the dependency is not supported.

First make sure all currently installed packages are up-to-date by running:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

Then re-run the check dependencies script. If that still hasn't fixed the issue then you need check each of the packages that are causing errors. One way of doing so is to run ipython and figure out where those files come from.

```
$ ipython
Python ...
Type "copyright", "credits" or "license" for more information.
...

In [1]: import pyewf

In [2]: pyewf.get_version()
Out[2]: u'20140608'

In [3]: pyewf.__file__
Out[3]: '/usr/lib/python2.7/dist-packages/pyewf.so'
```

Load the dependency that was causing the error. Check it's version, if it is part of the [libyal](https://github.com/libyal) collection use the ``LIBRARY.get_version()`` to get the version information, other libraries store their version information differently, most often you can call ``LIBRARY.__version__``.

If the version is the wrong out-of-date version you can always use the built-in ``LIBRARY.__file__`` to figure out where that file came from. The file can come from another Debian package or from a source installation. If this is coming from a source installation one way of removing it is to simply delete that particular file (or .egg directory). 

To find out which package a file belongs to, you can run:

```
$ dpkg -S /usr/lib/python2.7/dist-packages/pyewf.so
libewf-python: /usr/lib/python2.7/dist-packages/pyewf.so
```

Another example is *pyparsing* that has sometimes caused issues:

```
In [1]: import pyparsing

In [2]: pyparsing.__version__
Out[2]: '2.0.3'

In [3]: pyparsing.__file__
Out[3]: '/usr/lib/python2.7/dist-packages/pyparsing.pyc'

```

In this case the file returned back is the ".pyc" file, which is not included in the dpkg package:

```
$ dpkg -S /usr/lib/python2.7/dist-packages/pyparsing.pyc
dpkg-query: no path found matching pattern /usr/lib/python2.7/dist-packages/pyparsing.pyc
```

In order to find out which package this file belongs to remove the final "c" so it becomes ".py" instead of ".pyc", eg:

```
$ dpkg -S /usr/lib/python2.7/dist-packages/pyparsing.py
python-pyparsing: /usr/lib/python2.7/dist-packages/pyparsing.py
```

Once the package has been identified that contains the out-of-date dependency the next step is to see if it is truly at the latest version.

```
$ apt-cache policy python-construct
python-construct:
  Installed: 2.5.1-1
  Candidate: 2.5.1-1
  Version table:
     2.5.2-1 0
        500 REPO
 *** 2.5.1-1 0
        600 REPO
        100 /var/lib/dpkg/status
```

Here you can see an example of *python-construct* that has version **2.5.1-1** installed instead of version **2.5.2-1**, which is required by plaso. To correct this you may have to specifically indicate the version you want to install.

```
$ sudo apt-get install python-construct=2.5.2-1
```

### Common Issues

**Construct**

```
$ log2timeline.py 
Traceback (most recent call last):
  File "/usr/bin/log2timeline.py", line 13, in <module>
    from plaso.cli import extraction_tool
  File "/usr/lib/python2.7/dist-packages/plaso/cli/extraction_tool.py", line 7, in <module>
    from plaso.cli import storage_media_tool
...
  File "/usr/lib/python2.7/dist-packages/dfvfs/file_io/gzip_file_io.py", line 22, in GzipFile
    construct.ULInt16(u'signature'),
  File "/usr/lib/python2.7/dist-packages/construct/macros.py", line 160, in ULInt16
    return FormatField(name, "<", "H")
  File "/usr/lib/python2.7/dist-packages/construct/core.py", line 352, in __init__
    StaticField.__init__(self, name, self.packer.size)
  File "/usr/lib/python2.7/dist-packages/construct/core.py", line 324, in __init__
    Construct.__init__(self, name)
  File "/usr/lib/python2.7/dist-packages/construct/core.py", line 103, in __init__
    raise TypeError("name must be a string or None", name)
TypeError: ('name must be a string or None', u'signature')
```

This is an indication that construct is out-of-date. Please make sure you update to the latest version.

```
$ apt-cache policy python-construct
```

Check to see if there is a more up-to-date version available, you may need to specifically indicate the version you would like to install, eg:

```
$ sudo apt-get install python-construct=2.5.2-1
```

**PyParsing**

The following traceback:

```
=======================
Traceback (most recent call last):
File "/usr/bin/log2timeline.py", line 28, in <module>
from plaso.frontend import frontend
File "/usr/lib/python2.7/dist-packages/plaso/frontend/frontend.py", line 36, in <module>
...
pyparsing.lineEnd())
TypeError: __call__() takes exactly 2 arguments (1 given)
========================
```

This is indicative that you are running an old version of pyparsing. Please make sure you are using the latest version, see what is available using:

```
$ apt-cache policy python-pyparsing
```

And install the latest version.

**libewf**

There are some packages that declare **libewf2** as one of their dependencies. This is an out dated version of the [libewf](https://github.com/libyal/libewf) library provided by your distribution.

See for instance [this issue](https://github.com/log2timeline/plaso/issues/301).

The solution here is to remove the **libewf2** package from the system and replace it by **libewf** and **libewf2** packages from the GIFT PPA.

```
$ sudo apt-get remove libewf2
```

Note that this may remove other packages as well that depend on **libewf2**, which are likely to be out dated as well.

```
$ sudo apt-get install libewf libewf2=20140608
```

Installing **libewf2** from the GIFT PPA prevents your package manager installing its own version of the libewf2 package when it does not need to, since the files are provided by the **libewf** package.