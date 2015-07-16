**This page is work in progress.**

## How to get started

First determine which version of plaso is must suitable to your needs, for more information see [Releases and roadmap](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap)

### I know the good old Perl version

If you are one of those people that liked the old perl version of log2timeline but really would like to switch use all the nifty features of the Python version. Fear not, [here](https://github.com/log2timeline/plaso/wiki/Upgrading-From-0.x-Branch) is a guide to help you migrate.

### Upgrading from a previous version of plaso to 1.3

Plaso is still very much under development and you might notice that is changes significantly between versions. If you're upgrading from a previous version of plaso we recommend removing the previous version first, then install the version 1.3. 

## The Basics

The plaso package also comes with several command line tools, each with a specific purpose.

* image_export
* log2timeline
* pinfo
* [preg] (https://github.com/log2timeline/plaso/wiki/Using-preg)
* psort

Note that each tool can be invoked with a "``-h``" command line flag to display basic usage and command line option information. For more detailed information about a tool follow the links above.

### image_export

**image_export** is a command line tool to export file content from a storage media image or device based on various filter criteria, such as extension names, filter paths, file format signature identifiers, file creation date and time ranges, etc.

### log2timeline

**log2timeline** is a command line tool to extract [events](https://github.com/log2timeline/plaso/wiki/Scribbles-about-events#what-is-an-event) from individual files, recursing a directory (e.g. mount point) or storage media image or device. log2timeline creates a plaso storage file which can be analyzed with the pinfo and psort tools.

The plaso storage file contains the extracted events and various metadata about the collection process alongside information collected from the source data. It may also contain information about tags applied to events and reports from analysis plugins.

### pinfo

**pinfo** is a command line tool to provide information about the contents of a plaso storage file. 

### preg

**preg** is a front-end that demonstrates different use-case for plaso. **preg** only purpose is Windows Registry parsing. The front-end uses the Windows Registry parser and plugins from plaso and prints out reports or allows you to interactively interact with the content of the Registry file using a console.

### psort

**psort** is the post-processing tool used to filter, sort and process the plaso storage file produced by **log2timeline**. This is the tool that can be used for all post-processing filtering, sorting and potential automatic analysis of the storage file.