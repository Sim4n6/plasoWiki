**WIP**

**log2timeline** is a command line tool to extract [events](https://github.com/log2timeline/plaso/wiki/Scribbles-about-events#what-is-an-event) from individual files, recursing a directory (e.g. mount point) or storage media image or device. log2timeline creates a plaso storage file which can be analyzed with the pinfo and psort tools.

The plaso storage file contains the extracted events and various metadata about the collection process alongside information collected from the source data. It may also contain information about tags applied to events and reports from analysis plugins.

