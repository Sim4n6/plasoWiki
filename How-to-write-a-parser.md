# Introduction

This page is intended to give you an introduction into developing a parser for plaso.

* First a step-by-step example is provided to create a simple binary parser for the Safari Cookies.binarycookies file.
* At bottom are some common troubleshooting tips that others have run into before you.

This page assumes you have at least a basic understanding of programming in Python and use of git.

# Format

Before you can write a binary file parser you will need to have a good understanding of the file format. A description of the Safari Cookies.binarycookies format can be found [here](https://github.com/libyal/assorted/blob/master/documentation/Safari%20Cookies.asciidoc).

# Test data

First we make a representative test file and add it to the test_data/ directory, in our example:
```
test_data/Cookies.binarycookies
```

**Make sure that the test file does not contain sensitive or copyrighted material.**

# Parsers, events and formatters

## The parser

```
plaso/formatters/safari_cookies.py
```

```
# -*- coding: utf-8 -*-
"""Parser for Safari Binary Cookie files."""

from plaso.containers import time_events
from plaso.parsers import interface
from plaso.parsers import manager

class BinaryCookieEvent(time_events.CocoaTimeEvent):
  """A convenience class for a binary cookie event."""
  ...

class BinaryCookieParser(interface.FileObjectParser):
  """Parser for Safari Binary Cookie files."""
  ...


manager.ParsersManager.RegisterParser(BinaryCookieParser)
```

```
plaso/parsers/safari_cookies.py
```