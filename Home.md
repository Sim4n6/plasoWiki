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

Code coverage:
[![Coverage Status](https://img.shields.io/coveralls/log2timeline/plaso.svg)](https://coveralls.io/r/log2timeline/plaso?branch=master)

Also see:
* [Project documentation](http://plaso.kiddaland.net/)
* [Downloads](https://googledrive.com/host/0B30H7z4S52FleW5vUHBnblJfcjg/)
* Blog: [All things time related....](http://blog.kiddaland.net/)
* Mail group: [log2timeline-discuss](https://groups.google.com/forum/#!forum/log2timeline-discuss)
* Mail group: [log2timeline-dev](https://groups.google.com/forum/#!forum/log2timeline-dev)
* [log2timeline](http://plaso.kiddaland.net/usage/log2timeline/)