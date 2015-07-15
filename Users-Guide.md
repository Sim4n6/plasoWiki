**This page is work in progress.**

## How to get started

1. Determine which version of plaso is must suitable to your needs, for more information see [Releases and roadmap](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap)

## I know the good old Perl version

If you are one of those people that liked the old perl version of log2timeline but really would like to switch use all the nifty features of the Python version. Fear not, [here](https://github.com/log2timeline/plaso/wiki/Upgrading-From-0.x-Branch) is a guide to help you migrate.

## The Basics

Since plaso is really a back end, it needs a front-end to be able to run it as a stand-alone tool. There are few front-ends that are distributed with plaso, each with it's own purpose.

###log2timeline

**log2timeline** is the main front-end to the plaso back-end, a command line tool used to collect and correlate events extracted from a filesystem.

In other words, **log2timeline** is the tool that you use to parse a file, mount point, storage media file, to extract and correlate events from. These events can then later be analyzed.

###psort

**psort** is the post-processing tool used to filter, sort and process the plaso storage file produced by **log2timeline**. This is the tool that can be used for all post-processing filtering, sorting and potential automatic analysis of the storage file.

###pinfo

The plaso storage file does not only contain extracted events, it also contains various metadata about the collection process alongside information collected from the source data. It may also contain information about tags applied to events and reports from analysis plugins.

**pinfo** is the tool used to dump all the metadata stored inside the plaso storage file.

###preg

**preg** is a front-end that demonstrates different use-case for plaso. **preg** only purpose is Windows Registry parsing. The front-end uses the Windows Registry parser and plugins from plaso and prints out reports or allows you to interactively interact with the content of the Registry file using a console.

###image_export

**image_export** allows the user to export file content from a storage media file using various criteria, such as; extension names, filter paths, format signature identifiers, etc.

## How to use the tools

The first step is to use the "``-h``" flag to display the tools help page. The help page contains all the flags that can be used to control the tool and typically it ends with a quick demonstration of a use case.

After that, please refer to each tools specific site:
 + log2timeline
 + psort
 + pinfo
 + [preg] (https://github.com/log2timeline/plaso/wiki/Using-preg)
 + image_export

