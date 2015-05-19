**WARNING: this page is work in progress and some text might not reflect the current situation**

# Automated tests
Plaso comes with multiple forms of automated tests:

* unit tests
* end-to-end tests

## Unit tests
The unit tests are intended to detect issues after individual changes (change lists). Unit tests are typically small by nature and only test a specific part of the code.

The unit tests are stored in the `tests` sub directory, in the same directory hierarchy as the plaso module directory, and can be run with:
```
python run_tests.py
```

The unit tests are also run automatically on [Travis-CI](https://travis-ci.org/) and [AppVeyor](https://ci.appveyor.com) after every commit (code submit) to detect cross platform issues. 

## End-to-end tests
The end-to-end tests are intended to detect issues in how the various parts of plaso work together, e.g. can pinfo.py or psort.py read the plaso storage file created by log2timeline.py.

The end-to-end tests are divided in multiple parts:

* the test scripts
* the test sets

```
Projects/
  plaso/
    plaso/
    tests/
      test_extract_and_output.sh
    ...
  tests/
    .extract_and_output/
      test_set1/
        files
        options
        results/
          log2timeline.log.gz
          pinfo.log.gz
          psort.log.gz
          storage.plaso

      test_set2/
        files
        options
        results/

    test_set1/
      image.raw

    test_set2/
      test_dir/
        test.log
        test.Evtx
    ...
```

**TODO: write the result files somewhere for debugging**

In the example above the test scripts are stored in:
```
Projects/plaso/tests/
```

And the test sets in:
```
Projects/tests/
```

This directory contains multiple sub directories e.g.
```
Projects/tests/test_set1/
```

that is a test set directory and contains the the input (source) directory and files to run the tests on.

Or:
```
Projects/tests/.extract_and_output/
```

that is a test script configuration directory and per test set contains:

* previous test results used comparison
* the test set configuration
  * which files in the test set to test on
  * which options to use in the test script
