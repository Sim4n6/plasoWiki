# Style Guide

We primarily follow the [Google Python Style Guide](http://google-styleguide.googlecode.com/svn/trunk/pyguide.html). 

Various plaso specific additions/variations are:

 * Indent your code blocks with 2 spaces (not 4 as in the style guide). In the case of a hanging indent, use four spaces (according to the style guide).
 * Method and function names follow the following logic: <public> **CapWords()**, <internal> **_CapWords()** (protected) and <internal> **__CapWords()** (private)
 * Quote strings as ' or """ instead of "
   * Quote strings in command line arguments (argparse) as "
 * Textual strings should be Unicode strings and hence defined as u'string'
 * Use the format() function instead of the %-way of formatting strings.
   * Use positional or parameter format specifiers with typing e.g. '{0:s}' or '{text:s}' instead of '{0}', '{}' or '{:s}'. If we ever want to have language specific output strings we don't need to change the entire codebase (again). It also makes is easier in determining what type every parameter is expected to be.
 * Use class methods in preference of static methods
   * Use "cls" as the name of the class variable in preference of "klass"
 * When catching exceptions use "as exception:" not some alternative form like "as error:" or "as details:"
 * Use textual pylint overrides e.g. "# pylint: disable=no-self-argument" instead of "# pylint: disable=E0213". For a list of overrides see: http://docs.pylint.org/features.html


## Rationale behind style guide and code review

To keep the code base maintainable and readable all code is developed using a similar coding style. It ensures:

* the code is easy to maintain and understand. As a developer you'll sometimes find yourself thinking [WTF](http://en.wikipedia.org/wiki/WTF), what is the code supposed to do here. So it is really important point that you need to be able to come back to code 5 months later and still quickly understand what it supposed to be doing. Also for other people that want to contribute it is necessary that they need to be able to quickly understand the code. Be that said, quick-and-dirty solutions might work when you're working on a case, but we'll ban them from the code base.
* at least two eyes looked over the code in hopes of finding potential bugs or errors (before they become bugs and errors). This also improves the overall code quality.
* that every developer knows to (largely) expect the same coding style.

We've noticed that some people find the process of having a style guide and a code review process intimidating. We've also noticed that once people get used to it and have gone through the process few times they are generally thankful and learn quite a lot during the process, so bear with us.

**The short version:**

*don't be intimidated.*

**The longer version:**

One language is not the same as another, you might are fluent in C or Perl that does not mean the same for Python. You might have just started programming while others have been doing this for years. Our challenge is having a code base that is accessible and sufficiently uniform to most of you.

Also don't be intimidated by rewrites/refactors, which often feels the code base is changing under your feet. We have to make sure the code base is maintainable and a necessary evil there is to regular reshape and clean up things to get new features in.

We continuously try to improve the code base, including making things and easier and quicker to write which sometimes means that the way you just learned might already superseded by another. We try to keep the documentation up to date but this sometimes be after you ran into an issue.

First time contributors may come across the fact that the code review process actually takes quite a long time, with lots of back and forth comments. You may think that you are wasting the core developers time, but rest assured you are not. We look at this as an investment of building up good solid code contributors. We would like to make sure our contributors understand the code and the style guide and will make suggestions to the contributor to fix what we think needs improving. Despite spending potentially more time to begin with to get code submitted into the project we believe this investment in code review will result in better code submissions and increased proficiency of the contributor.

Therefore we would like to ask people to hang on, to get through the code review process and try to learn something while going through it. Rest assured, it will get easier next time and even easier the time after that, and before you know it you can contribute code to the project with little to no comments.

And if things are unclear, don't hesitate to ask. The developer mailing list is: log2timeline-dev@googlegroups.com

