plaso (Plaso Langar Að Safna Öllu) is a Python-based backend engine for the tool log2timeline. 

log2timeline is a tool designed to extract timestamps from various files found on a typical computer system(s) and aggregate them.

The initial purpose of plaso was to have the timestamps in a single place for computer forensic analysis (aka Super Timeline).

However plaso has become a framework that supports:
* adding new parsers or parsing plug-ins;
* adding new analysis plug-ins;
* writing one-off scripts to automate repetitive tasks in computer forensic analysis or equivalent.

And is moving to support:
* adding new general purpose parses/plugins that may not have timestamps associated to them;
* adding more analysis context;
* allowing more targeted approach to the collection/parsing.

### Project status
[Travis-CI](https://travis-ci.org/) | [AppVeyor](https://ci.appveyor.com) | [Coveralls](https://coveralls.io/)
--- | --- | --- 
[![Build Status](https://travis-ci.org/log2timeline/plaso.svg?branch=master)](https://travis-ci.org/log2timeline/plaso) | [![Build status](https://ci.appveyor.com/api/projects/status/g3x5ylegjjo61p4m?svg=true)](https://ci.appveyor.com/project/joachimmetz/plaso) | [![Coverage Status](https://img.shields.io/coveralls/log2timeline/plaso.svg)](https://coveralls.io/r/log2timeline/plaso?branch=master)

### Also see

* [Project documentation](http://plaso.kiddaland.net/)
  * [Developers Guide](https://github.com/log2timeline/plaso/wiki/Developers-Guide)
  * [Users Guide](https://github.com/log2timeline/plaso/wiki/Users-Guide)
* [Downloads](https://googledrive.com/host/0B30H7z4S52FleW5vUHBnblJfcjg/)
* Blog: [All things time related....](http://blog.kiddaland.net/)
* Mailing lists:
  * For general discussions: [log2timeline-discuss](https://groups.google.com/forum/#!forum/log2timeline-discuss)
  * For development: [log2timeline-dev](https://groups.google.com/forum/#!forum/log2timeline-dev)
* [log2timeline](http://plaso.kiddaland.net/usage/log2timeline/)