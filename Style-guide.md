# Style Guide

We primarily follow the [Google Python Style Guide](http://google-styleguide.googlecode.com/svn/trunk/pyguide.html). 

Various plaso specific additions/variations are:

 * Indent your code blocks with 2 spaces (not 4 as in the style guide). In the case of a hanging indent, use four spaces (according to the style guide).
 * Method and function names follow the following logic: <public> **CapWords()**, <internal> **_CapWords()** (protected) and <internal> **__CapWords()** (private). Acronyms and initialisms should be preserved, eg HTMLParser, and not HtmlParser.
 * Quote strings as ' or """ instead of "
   * Quote strings in command line arguments (argparse) as "
 * Textual strings should be Unicode strings and hence defined as u'string'
 * Use the format() function instead of the %-way of formatting strings.
   * Use positional or parameter format specifiers with typing e.g. '{0:s}' or '{text:s}' instead of '{0}', '{}' or '{:s}'. If we ever want to have language specific output strings we don't need to change the entire codebase (again). It also makes is easier in determining what type every parameter is expected to be.
 * Use class methods in preference of static methods
   * Use "cls" as the name of the class variable in preference of "klass"
 * When catching exceptions use "as exception:" not some alternative form like "as error:" or "as details:"
 * Use textual pylint overrides e.g. "# pylint: disable=no-self-argument" instead of "# pylint: disable=E0213". For a list of overrides see: http://docs.pylint.org/features.html

Also see: [Python 3 Guide](https://github.com/log2timeline/plaso/wiki/Python-3-Guide)

## Rationale

To keep the code base maintainable and readable all code is developed using a similar coding style. It ensures:

* the code is easy to maintain and understand. As a developer you'll sometimes find yourself thinking [WTF](http://en.wikipedia.org/wiki/WTF), what is the code supposed to do here. So it is really important point that you need to be able to come back to code 5 months later and still quickly understand what it supposed to be doing. Also for other people that want to contribute it is necessary that they need to be able to quickly understand the code. Be that said, quick-and-dirty solutions might work when you're working on a case, but we'll ban them from the code base.
* that every developer knows to (largely) expect the same coding style.

We've noticed that some people find the process of having a style guide and a code review process intimidating. We've also noticed that once people get used to it and have gone through the process few times they are generally thankful and learn quite a lot during the process, so bear with us.

Having a unified style makes it much easier to maintain the codebase. That means that every developer should be able to make changes in any file in the codebase without worrying about different code styles. 

And if things are unclear, don't hesitate to ask. The developer mailing list is: log2timeline-dev@googlegroups.com
