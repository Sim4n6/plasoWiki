* [Setting up and maintaining your development environment](https://github.com/log2timeline/plaso/wiki/Developers-Guide#setting-up-and-maintaining-your-development-environment)
* [Getting Started](https://github.com/log2timeline/plaso/wiki/Developers-Guide#getting-started)
* [Design](https://github.com/log2timeline/plaso/wiki/Developers-Guide#design)
* [Roadmap](https://github.com/log2timeline/plaso/wiki/Developers-Guide#roadmap)
* [Contributing Code](https://github.com/log2timeline/plaso/wiki/Developers-Guide#contributing-code)

## Setting up and maintaining your development environment

The first challenge you will encounter is setting up and maintaining your development environment.

**Note that plaso and some dependencies are currently actively under development keeping up with the development release is not for "the faint of heart".**

* [Running the development release on Ubuntu Linux](https://github.com/log2timeline/plaso/wiki/Development-release-Ubuntu)
  * [Building and installing dependencies on Ubuntu Linux](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu)
* [Running the development release on Fedora Core Linux](https://github.com/log2timeline/plaso/wiki/Development-release-Fedora-Core)
  * [Building and installing dependencies on Fedora Core Linux](https://github.com/log2timeline/plaso/wiki/Dependencies-Fedora-Core)
* [Running the development release on Mac OS X](https://github.com/log2timeline/plaso/wiki/Development-release-MacOS)
  * [Building and installing dependencies on Mac OS X](https://github.com/log2timeline/plaso/wiki/Dependencies-Mac-OS-X)
* [Running the development release on Windows](https://github.com/log2timeline/plaso/wiki/Development-release-Windows)
  * [Building and installing dependencies on Windows](https://github.com/log2timeline/plaso/wiki/Dependencies-Windows)

## Getting Started

Once you've set up your development environment we recommend start simple:

* [How to write a parser](https://github.com/log2timeline/plaso/wiki/How-to-write-a-parser)
* [How to write a parser plugin](https://github.com/log2timeline/plaso/wiki/How-to-write-a-parser-plugin)
* [How to write an analysis plugin](https://github.com/log2timeline/plaso/wiki/How-to-write-an-analysis-plugin)
* [How to write an output module](https://github.com/log2timeline/plaso/wiki/How-to-write-an-output-module)

## Design
Overview of the general architecture of plaso:

* [Architecture](https://github.com/log2timeline/plaso/wiki/Internals)
* [Source code and API documentation](http://plaso-api.readthedocs.org/en/latest/modules.html)

## Roadmap

A high level roadmap can be found [here](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap). Individual features are tracked as a github issue and labeled as "enhancement". A list of features can be found [here](https://github.com/log2timeline/plaso/issues?q=is%3Aopen+is%3Aissue+label%3Aenhancement).

## Contributing Code

Want to add a parser to plaso and you are ready to go? Start by checking [here](https://github.com/log2timeline/plaso/issues?q=is%3Aopen+is%3Aissue+label%3Aenhancement) if someone is already working on it. If you don't see anything there you can just go ahead and [create an issue on the github site](https://github.com/log2timeline/plaso/issues) and mark it as "enhancement". Assign the issue to yourself so that we can keep track on who is working on what.

If you cannot program and still have a great idea for a feature please go ahead and create an issue and leave it unassigned, note that the priority will be who ever wants to work on it. Or consider this the idea opportunity to learn yourself Python programming.

Before you start writing the code, please review the following:

* [Style guide](https://github.com/log2timeline/plaso/wiki/Style-guide). All code submitted to the project needs to follow this style guide.
* [Code review](https://github.com/log2timeline/plaso/wiki/Codereview). All code that is submitted into the project needs to be reviewed by at least one other person.
* [Adding a new dependency](https://github.com/log2timeline/plaso/wiki/Adding-a-new-dependency). If your code requires adding a new dependency please check out these instructions.

### Before you submit your first code review

1. Join the development mailing list: [log2timeline-dev@googlegroups.com](https://groups.google.com/forum/?fromgroups#!forum/log2timeline-dev), we recommend using the same account as step 1
2. Install the required development tools like pylint, python-mock, sphinx
3. Make sure to run all the tests inside the plaso and the dfVFS codebase, and that they successfully complete on your development system
4. Make sure your development system is set up correctly so that you can develop and test correctly.
5. Make sure your email address and name are correctly set in git e.g.:
```
git config --global user.name "Full Name"
git config --global user.email name@example.com
git config --global push.default matching
```

Use `git config -l` to determine the current configuration.


### Core features changes

Sometimes you need to make some change to the core of the plaso codebase. In those cases we ask that contributors first create a short design doc explaining the rationale behind the change. The design doc needs to contain:

1. Describe the problem you are facing
2. List the objectives of this change
3. Mention what is in scope and what's not
4. Describe the solution/proposal

The preferred way of creating these design docs is to use Google Docs and send the link to the development mailing list so that it can be discussed further **before** starting to implement the code.

The current design docs are [stored here](https://drive.google.com/folderview?id=0B3fBvzttpiiSQW16cFhNTUtXVGM&usp=sharing). You may not have access to that folder, so you may need to request access to it.

### Tests

Tests are part of a maintainable code base. Code without sufficient test is very likely to be broken by a large rewrite/refactor.

Some guidelines for writing tests: [Style guide - tests](https://github.com/log2timeline/plaso/wiki/Style-guide#tests)
