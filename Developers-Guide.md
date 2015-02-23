**This page is work in progress.**

For the current version of the documentation see: https://sites.google.com/a/kiddaland.net/plaso/developer

## Design
* [Architecture](https://sites.google.com/a/kiddaland.net/plaso/developer/architecture)

### Roadmap
A read-only version of the roadmap document can be found here: [Plaso - Roadmap and Assignment](http://goo.gl/cRjA7y). The roadmap document displays the current status, who's working on the parser, etc.

**Note that this is a general wish list, that may not be completely up-to-date.**

## Setting up and maintaining your development environment
The first challenge you will encounter is setting up and maintaining your development environment.

**Note that plaso and some dependencies are currently actively under development keeping up with the development release is not for "the faint of heart".**

* [Running the development release on Ubuntu Linux](https://github.com/log2timeline/plaso/wiki/Development-release-Ubuntu)
  * [Building and installing dependencies on Ubuntu Linux](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu)
* [Running the development release on Fedora Core](https://github.com/log2timeline/plaso/wiki/Development-release-Fedora-Core)
  * [Building and installing dependencies on Fedora Core](https://github.com/log2timeline/plaso/wiki/Dependencies-Fedora-Core)
* [Running the development release on Mac OS X](https://github.com/log2timeline/plaso/wiki/Development-release-Mac-OS-X)
  * [Building and installing dependencies on Mac OS X](https://github.com/log2timeline/plaso/wiki/Dependencies-Mac-OS-X)
* [Running the development release on Windows](https://github.com/log2timeline/plaso/wiki/Development-release-Windows)
  * [Building and installing dependencies on Windows](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu)

## Getting started writing code
* [How to write a parser](https://sites.google.com/a/kiddaland.net/plaso/developer/parsers)

## Contributing
Want to add a parser to plaso and you are ready to go you can just go ahead and edit: [Plaso - Roadmap and Assignment](http://goo.gl/IIs4HM) and assign the task of writing a new parser to yourself. Please add a date so we can reassign if it turns out you don't have time.

If you cannot program and still have a great idea for a feature please go ahead and edit, note that the priority will be who ever wants to work on it. Or consider this the idea opportunity to learn yourself Python programming.

* [Style guide](https://github.com/log2timeline/plaso/wiki/Style-guide)
* Code review

### Rational behind style guide and code review
To keep the code base maintainable and readable all code is developed using a similar coding style. It ensures:

* the code is easy to maintain and understand. As a developer you'll sometimes find yourself thinking [WTF](http://en.wikipedia.org/wiki/WTF), what is the code supposed to do here. So it is really important point that you need to be able to come back to code 5 months later and still quickly understand what it supposed to be doing. Also for other people that want to contribute it is necessary that they need to be able to quickly understand the code. Be that said, quick-and-dirty solutions might work when you're working on a case, but we'll ban them from the code base.
* at least two eyes looked over the code in hopes of finding potential bugs or errors (before they become bugs and errors). This also improves the overall code quality.
* that every developer knows to (largely) expect the same coding style.

We've noticed that some people find the process of having a style guide and a code review process intimidating.

**The short version:**

don't be intimidated.

**The longer version:**

One language is not the same as another, you might are fluent in C or Perl that does not mean the same for Python. You might have just started programming while others have been doing this for years. Our challenge is having a code base that is accessible and sufficiently uniform to most of you.

Also don't be intimidated by rewrites/refactors, which often feels the code base is changing under your feet. We have to make sure the code base is maintainable and a necessary evil there is to regular reshape and clean up things to get new features in.

We continuously try to improve the code base, including making things and easier and quicker to write which sometimes means that the way you just learned might already superseded by another. We try to keep the documentation up to date but this sometimes be after you ran into an issue.

First time contributors may come across the fact that the code review process actually takes quite a long time, with lots of back and forth comments. You may think that you are wasting the core developers time, but rest assured you are not. We look at this as an investment of building up good solid code contributors. We would like to make sure our contributors understand the code and the style guide and will make suggestions to the contributor to fix what we think needs improving. Despite spending potentially more time to begin with to get code submitted into the project we believe this investment in code review will result in better code submissions and increased proficiency of the contributor.

Therefore we would like to ask people to hang on, to get through the code review process and try to learn something while going through it. Rest assured, it will get easier next time and even easier the time after that, and before you know it you can contribute code to the project with little to no comments.

And if things are unclear, don't hesitate to ask. The developer mailing list is: log2timeline-dev@googlegroups.com

### Submitting code
There can be a code freeze announced before a release, in which we try to focus on testing and bug fixes. In such a freeze, new features will added to the codebase after the release.

**TODO: add more text**