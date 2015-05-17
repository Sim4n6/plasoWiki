**This page is work in progress.**

## Design
Overview of the general architecture of plaso:

* [Architecture](https://sites.google.com/a/kiddaland.net/plaso/developer/architecture)
* [Source code and API documentation](http://plaso-api.readthedocs.org/en/latest/modules.html)

## Roadmap

The roadmap is currently tracked in the github issue list and labeled as "enhancement". The list can be found [here](https://github.com/log2timeline/plaso/issues?q=is%3Aopen+is%3Aissue+label%3Aenhancement).

A read-only version of the older roadmap document can be found here: [Plaso - Roadmap and Assignment](http://goo.gl/cRjA7y). The roadmap document displays the current status, who's working on the parser, etc. Keep in mind though that this roadmap is no longer maintained and is therefore not up-to-date, however there may still be things in the old roadmap that have not yet been transferred over to the github site.

## Setting up and maintaining your development environment
The first challenge you will encounter is setting up and maintaining your development environment.

**Note that plaso and some dependencies are currently actively under development keeping up with the development release is not for "the faint of heart".**

* [Running the development release on Ubuntu Linux](https://github.com/log2timeline/plaso/wiki/Development-release-Ubuntu)
  * [Building and installing dependencies on Ubuntu Linux](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu)
* [Running the development release on Fedora Core Linux](https://github.com/log2timeline/plaso/wiki/Development-release-Fedora-Core)
  * [Building and installing dependencies on Fedora Core Linux](https://github.com/log2timeline/plaso/wiki/Dependencies-Fedora-Core)
* [Running the development release on Mac OS X](https://github.com/log2timeline/plaso/wiki/Development-release-Mac-OS-X)
  * [Building and installing dependencies on Mac OS X](https://github.com/log2timeline/plaso/wiki/Dependencies-Mac-OS-X)
* [Running the development release on Windows](https://github.com/log2timeline/plaso/wiki/Development-release-Windows)
  * [Building and installing dependencies on Windows](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu)

### Prerequisites

1. Go to https://codereview.appspot.com to setup your account, you'll need a Google account for this.
2. Join the development mailing list: log2timeline-dev@googlegroups.com (https://groups.google.com/forum/?fromgroups#!forum/log2timeline-dev), we recommend using the same account as step 1
2. Install the required development tools like pylint, python-mock
3. Make sure to run all the tests inside the plaso codebase and the dfvfs one, and that they successfully complete on your development system
4. Get yourself added as a committer on the plaso git repo: https://github.com/orgs/log2timeline/teams/plaso-contribs
5. Make sure your development system is set up correctly so that you can push code to github. See: https://github.com/log2timeline/plaso
6. Make sure your email address and name are correctly set in git e.g.:
```
git config --global user.name "Full Name"
git config --global user.email name@example.com
git config --global push.default matching
```

Use `git config -l` to determine the current configuration.


## Contributing Code

Want to add a parser to plaso and you are ready to go? Start by checking [here](https://github.com/log2timeline/plaso/issues?q=is%3Aopen+is%3Aissue+label%3Aenhancement) if someone is already working on it. If you don't see anything there you can just go ahead and [create an issue on the github site](https://github.com/log2timeline/plaso/issues) and mark it as "enhancement". Assign the issue to yourself so that we can keep track on who is working on what.

If you cannot program and still have a great idea for a feature please go ahead and create an issue and leave it unassigned, note that the priority will be who ever wants to work on it. Or consider this the idea opportunity to learn yourself Python programming.

Before you start writing the code, please review the following:

* [Style guide](https://github.com/log2timeline/plaso/wiki/Style-guide). All code submitted to the project needs to follow this style guide.
* [Code review](https://github.com/log2timeline/plaso/wiki/Codereview). All code that is submitted into the project needs to be reviewed by at least one other person.
* [Adding a new dependency](https://github.com/log2timeline/plaso/wiki/Adding-a-new-dependency). If your code requires adding a new dependency please check out these instructions.

### Getting Started

Good way to learn how to write some code for plaso is to start easy, with a plugin or a parser. We have prepared codelabs to make the barrier of entry easier.

* [Codelabs] (https://github.com/log2timeline/codelabs/wiki)
* [How to write a parser](https://sites.google.com/a/kiddaland.net/plaso/developer/parsers)

### Larger Features Changing Core Codebase

Sometimes you need to make some change to the core of the plaso codebase. In those cases we ask that contributors first create a short design doc explaining the rationale behind the change. The design doc needs to contain:

1. Describe the problem you are facing
2. List the objectives of this change
3. Mention what is in scope and what's not
4. Describe the solution/proposal

The preferred way of creating these design docs is to use Google Docs and send the link to the development mailing list so that it can be discussed further **before** starting to implement the code.

The current design docs are [stored here] (https://drive.google.com/folderview?id=0B3fBvzttpiiSQW16cFhNTUtXVGM&usp=sharing). You may not have access to that folder, so you may need to request access to it.

### Tests

Tests are part of a maintainable code base. Code without sufficient test is very likely to be broken by a large rewrite/refactor.

Some guidelines for writing tests:

* Use as much as possible the test functions available in the local test_lib.py instead of writing your own test functions. If you think a test function is missing please mail the developer list.
* Use timelib.Timestamp.CopyFromString() for calculating expected timestamp values.

Common test code should be stored in "test library" files, e.g. the parser test library:

    plaso/parsers/test_lib.py

We do this for various reasons:

* to remove code duplication in "boiler plate" test code;
* to make the tests more uniform in both look-and-feel but also what is tested;
* improve test coverage;
* isolate core functionality from tests to prevent some future core changes affecting the parsers and plugins too much.
