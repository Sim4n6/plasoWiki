We primarily follow the [Google Python Style Guide](http://google-styleguide.googlecode.com/svn/trunk/pyguide.html). Various plaso specific additions/variations are:

* Indent your code blocks with 2 spaces (not 4 as in the style guide). In the case of a hanging indent, use four spaces (according to the style guide).
* Method and function names follow the following logic: <public> CapWords(), <internal> _CapWords() (protected) or __CapWords() (private)
* Quote strings as ' or """ instead of "
  * Quote strings in command line arguments (argparse) as "
* Textual strings should be Unicode strings and hence defined as u'string'
* Use the format() function instead of the %-way of formatting strings.
  * Use positional or parameter format specifiers with typing e.g. '{0:s}' or '{text:s}' instead of '{0}', '{}' or '{:s}'. If we ever want to have language specific output strings we don't need to change the entire codebase (again). It also makes is easier in determining what type every parameter is expected to be.
* Use class methods in preference of static methods
  * Use "cls" as the name of the class variable in preference of "klass"
* When catching exceptions use "as exception:" not some alternative form like "as error:" or "as details:"
* Use textual pylint overrides e.g. "# pylint: disable=no-self-argument" instead of "# pylint: disable=E0213". For a list of overrides see: http://docs.pylint.org/features.html


## Tests
Tests are part of a maintainable code base. Code without sufficient test is very likely to be broken by a large rewrite/refactor.

Some guidelines for writing tests:

* Use as much as possible the test functions available in the local test_lib.py instead of writing your own test functions. If you think a test function is missing please mail the developer list.
* Use timelib_test.CopyStringToTimestamp() for calculating expected timestamp values.

Common test code should be stored in "test library" files, e.g. the parser test library:
```
plaso/parsers/test_lib.py
```

We do this for various reasons:

* to remove code duplication in "boiler plate" test code;
* to make the tests more uniform in both look-and-feel but also what is tested;
* improve test coverage;
* isolate core functionality from tests to prevent some future core changes affecting the parsers and plugins too much.
