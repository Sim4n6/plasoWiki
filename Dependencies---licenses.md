**TODO this page is work in progress**

Original information: https://sites.google.com/a/kiddaland.net/plaso/developer/building-the-tool/licenses

Although plaso is licensed under the Apache License 2.0, binary builds of plaso include third party code that have been made available under various licenses.

Dependency | License
--- | --- 
[bencode](https://pypi.python.org/pypi/bencode) | BitTorrent Open Source License
[binplist](https://code.google.com/p/binplist/) | Apache License 2.0
[construct](http://construct.readthedocs.org/en/latest/) | MIT license
[DPKT](https://code.google.com/p/dpkt/) | [BSD 3-clause](https://code.google.com/p/dpkt/source/browse/trunk/LICENSE)
[Hachoir](https://bitbucket.org/haypo/hachoir) | GNU General Public License 2 <br> **Not integrated in the binary build.**
[IPython](http://ipython.org/) | BSD 3-clause license <br> PyReadline is considered part of IPython.
[Libprotobuf and Python-bindings](https://github.com/google/protobuf) | BSD 3-clause license
[LibYAML and Python-bindings](http://pyyaml.org/wiki/LibYAML) | MIT license
[Libesedb and Python-bindings](https://github.com/libyal/libesedb/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libevt and Python-bindings](https://github.com/libyal/libevt/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libevtx and Python-bindings](https://github.com/libyal/libevtx/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libfwsi and Python-bindings](https://github.com/libyal/libfwsi/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Liblnk and Python-bindings](https://github.com/libyal/liblnk/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libmsiecf and Python-bindings](https://github.com/libyal/libmsiecf/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libolecf and Python-bindings](https://github.com/libyal/libolecf/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libregf and Python-bindings](https://github.com/libyal/libregf/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libvshadow and Python-bindings](https://github.com/libyal/libvshadow/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Six](https://pypi.python.org/pypi/six/) | MIT license
[Sqlite](http://www.sqlite.org/index.html) | Public Domain
[Psutil](https://code.google.com/p/psutil/) | BSD 3-clause license
[Python](http://www.python.org/) | See: http://docs.python.org/2/license.html
[Python dateutil](http://labix.org/python-dateutil) | BSD 3-clause license
[Pyparsing](http://pyparsing.wikispaces.com/) | MIT license
[Pyelasticsearch](https://github.com/rhec/pyelasticsearch/) | 
[Pysqlite](https://pypi.python.org/pypi/pysqlite) | zlib/libpng license
[pytz](http://pytz.sourceforge.net/) | MIT license
[pywin32](http://pywin32.sourceforge.net/) | Python Software Foundation License <br> **Windows build only**

Dependency | License
--- | --- 
[dfVFS](https://github.com/log2timeline/dfvfs/) | Apache License 2.0
[Libbde and Python-bindings](https://github.com/libyal/libbde/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libewf and Python-bindings](https://github.com/libyal/libewf/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libqcow and Python-bindings](https://github.com/libyal/libqcow/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libsigscan and Python-bindings](https://github.com/libyal/libsigscan/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libsmdev and Python-bindings](https://github.com/libyal/libsmdev/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libsmraw and Python-bindings](https://github.com/libyal/libsmraw/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libvhdi and Python-bindings](https://github.com/libyal/libvhdi/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Libvmdk and Python-bindings](https://github.com/libyal/libvmdk/) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)
[Pytsk](https://code.google.com/p/pytsk/) | Apache License 2.0
[SleuthKit](http://www.sleuthkit.org/) | The SleuthKit is multi licensed <br> Common Public License 1.0; applies to most of the code <br> IBM Public License 1.0; applies to the file system code (tsk/fs, tools/fstools) <br> GNU General Public License 2; applies to srch_strings which **should not be included in a binary build of plaso**.
[talloc](http://talloc.samba.org/talloc/doc/html/index.html) | [GNU Lesser General Public License 3](http://www.gnu.org/licenses/lgpl.html)

Dependency | License
--- | --- 
[PyInstaller](http://www.pyinstaller.org/) | GNU General Public License 2 with an exception for the bootloader, which is the part that is used in plaso binaries.

# To do
Dependencies not mentioned explicitly yet:

* zlib (used in libqcow and libewf)
* openssl (used in libqcow and libewf)
* bzip2 (or part of python)
* Visual studio runtime dlls
