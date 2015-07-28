**This page is still WIP**

# psort

**psort** is a command line tool to post-process plaso storage files. It allows you to filter, sort and run automatic analysis on the contents of plaso storage files.

## Usage

To see a list of all available parameters you can pass to psort use ``-h`` or ``--help``.

The simplest way to run the tool is simply provide it with a storage file.

```
$ psort.py test.plaso
```

This will use the default output module and print out to STDOUT a list of all extracted events, merging detected duplicate events. All timestamps on the output will be in UTC.

The generic options are:

```
$ psort.py [-a] [-o FORMAT] [-w OUTPUTFILE] [-z TIMEZONE] STORAGE_FILE FILTER
```

### Output

To see a list of all supported output modules use the ``-o list`` switch:

```
$ psort.py -o list

******************************** Output Modules ********************************
4n6time_mysql : MySQL database output for the 4n6time tool.
4n6time_sqlite : Saves the data in a SQLite database, used by the tool 4n6time.
   dynamic : Dynamic selection of fields for a separated value output format.
   elastic : Saves the events into an ElasticSearch database.
      json : Saves the events into a JSON format.
 json_line : Saves the events into a JSON line format.
    l2tcsv : CSV format used by legacy log2timeline, with 17 fixed fields.
    l2ttln : Extended TLN 7 field | delimited output.
      null : An output module that doesn't output anything.
  pstorage : Dumps event objects to a plaso storage file.
     rawpy : "raw" (or native) Python output.
timesketch : Create a Timesketch timeline.
       tln : TLN 5 field | delimited output.
--------------------------------------------------------------------------------
```

If you are missing any optional dependencies not all output modules may be available, which would be displayed by the ``-o list`` switch:

```
******************************** Output Modules ********************************
4n6time_sqlite : Saves the data in a SQLite database, used by the tool 4n6time.
   dynamic : Dynamic selection of fields for a separated value output format.
      json : Saves the events into a JSON format.
 json_line : Saves the events into a JSON line format.
    l2tcsv : CSV format used by legacy log2timeline, with 17 fixed fields.
    l2ttln : Extended TLN 7 field | delimited output.
      null : An output module that doesn't output anything.
  pstorage : Dumps event objects to a plaso storage file.
     rawpy : "raw" (or native) Python output.
       tln : TLN 5 field | delimited output.
--------------------------------------------------------------------------------

*************************** Disabled Output Modules ****************************
4n6time_mysql : MySQL database output for the 4n6time tool.
   elastic : Saves the events into an ElasticSearch database.
timesketch : Create a Timesketch timeline.
--------------------------------------------------------------------------------
```

To change the output simply use the ``-o FORMAT``, eg:

```
$ psort.py -o l2tcsv test.plaso
```

This would use the "l2tcsv" module, or the default CSV output of the older Perl version of log2timeline.


MISSING MENTION OF ``-w FILENAME`` and ``-z TIMEZONE`` and ``-q``


### Automatic Analysis

DISCUSS
```
--analysis
```

### Filtering

DISCUSS
```
--slice DATE
--slice_size SLICE_SIZE
--slicer

FILTER
```

### Other options

DISCUSS
```
--data PATH
-a --include_all
--language LANGUAGE
```

#### Redirect Output

To redirect the output of the output modules, those that print to a regular file, use the ``-w FILENAME`` parameter, this redirects the output from STDOUT to the provided path.

```
$ psort.py -w timeline.csv test.plaso
```

To redirect logging information to another file instead of being printed to STDERR use the ``--logfile`` parameter.

```
$ psort.py --logfile output.log -w timeline.csv test.plaso
```

#### Debug

If during the runtime of **psort** the tool encounters an unexpected exception the debug mode can be used. To invoke debug mode use the ``-d`` parameter. What that will do is that instead of exiting the tool when an unexpected exception is raised it prints the traceback of the exception and drops into a [Python debug shell](http://stackoverflow.com/questions/4228637/getting-started-with-the-python-debugger-pdb). This can be used to debug the problem and fix the issue.
