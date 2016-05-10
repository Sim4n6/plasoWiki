## Code Review

All code submitted into the plaso project goes through code review. We use the tool Rietveld available on [codereview.appspot.com](https://codereview.appspot.com), which may not be perfect but we consider it good enough for our purposes.

One helpful hint is while you have a code in code review monitor the development mailing list for large changes or new dependencies that may potentially affect your code. Such changes may include code re-factors that change plugin interface while you have a plugin in review. These should be rare but they do happen every now and then.

### Rationale

To keep the code base maintainable and readable all code is developed using a similar coding style. See the [style guide](https://github.com/log2timeline/plaso/wiki/Style-guide). This makes the code easier to maintain and understand.

The purpose of the code review is to ensure that:

 * at least two eyes looked over the code in hopes of finding potential bugs or errors (before they become bugs and errors). This also improves the overall code quality.
 * make sure the code adheres to the style guide (we do have a linter but that is not perfect).
 * review design decisions and if needed assist with making the code more optimal or error tolerant.

**The short version:**

*don't be intimidated.*

**The longer version:**

One language is not the same as another, you might are fluent in C or Perl that does not mean the same for Python. You might have just started programming while others have been doing this for years. Our challenge is having a code base that is accessible and sufficiently uniform to most of you.

Also don't be intimidated by rewrites/refactors, which often feels the code base is changing under your feet. We have to make sure the code base is maintainable and a necessary evil there is to regular reshape and clean up things to get new features in.

We continuously try to improve the code base, including making things and easier and quicker to write which sometimes means that the way you just learned might already superseded by another. We try to keep the documentation up to date but this will sometimes be after you ran into an issue.

First time contributors may come across the fact that the code review process actually takes quite a long time, with lots of back and forth comments. You may think that you are wasting the core developers time, but rest assured you are not. We look at this as an investment of building up good solid code contributors. We would like to make sure our contributors understand the code and the style guide and will make suggestions to the contributor to fix what we think needs improving. Despite spending potentially more time to begin with to get code submitted into the project we believe this investment in code review will result in better code submissions and increased proficiency of the contributor.

Therefore we would like to ask people to hang on, to get through the code review process and try to learn something while going through it. Rest assured, it will get easier next time and even easier the time after that, and before you know it you can contribute code to the project with little to no comments.

And if things are unclear, don't hesitate to ask. The developer mailing list is: log2timeline-dev@googlegroups.com

### Why not use github pull requests?

Although github pull requests are convenient for small code reviews they are not very well suited for larger ones. It is also not a very efficient User Interface/Experience on the reviewer side.

Another downside of using github pull requests are that they convolute the commit history and we really don't want to have contributors have to extensively study git first before being able to commit to the project. [More discussion on the matter.](http://blog.spreedly.com/2014/06/24/merge-pull-request-considered-harmful/)

### Why not use reviewable.io?

We have looked at [reviewable.io](https://reviewable.io) and our current assessment is that it looks very nice but does not make for a very functional User Interface/Experience. It also convolutes the git commit history.

### How it Works

The code review workflow predates plaso's move to github. We are in the process of adding support for a more github aligned workflow. To be able to use the advantages github offers without having to fight against its limitations.

See: [Code review process](https://github.com/log2timeline/l2tdocs/blob/master/process/Code%20review%20process.asciidoc)

#### Referencing github issues

If your changes relate to a specific [github issue](https://github.com/log2timeline/plaso/issues) add the issue number as following:

```
Added serializers profiler #120
```

Where the "#120" is a reference to issue number 120.

#### Nobrowser

If you are developing the code from a computer that does not have a browser installed, or you are accessing the development machine remotely you need to supply the `--nobrowser` command line argument and then visit the [following site](https://codereview.appspot.com/get-access-token) on a computer with a browser.

This will create an OAuth token that you can copy paste to the terminal window.

#### Starting a code review

If everything goes well the script will report the code review (or change list (CL)) created on Rietveld e.g.:
```
Issue created: URL: http://codereview.appspot.com/6811077
```

The details of the code review can be changed at a later point in time via that URL.

The creation of the code review will also send an email the [developer mailing list](https://groups.google.com/forum/#!forum/log2timeline-dev), notifying people that there is a code review pending and it will show up in the reviewers queue on the Rietveld site.

#### Updating the code review

During the code review process you'll be asked to change few things, that is the reviewer will add comments. Please follow the following guideline during the code review process:

* Answer **ALL** comments made in the code review, even if it is only an ACK or "Done".
  * It is also necessary to publish the comments, otherwise the reviewer doesn't see the answers.
  * On the codereview site hit "m" for "Publish+Mail Comments" so that the review gets updated alongside the newly updated code.
* Make the necessary changes to the code, as suggested by the reviewer.
* Make sure you have not checked in the changes locally (as in not executed `git commit`").

When all code changes have been completed and you are ready for another round execute:
```
./utils/update.sh [--nobrowser]
```

If you are running the `update.sh` script off a github fork make sure all changes have been committed and pushed to your fork before running `update.sh`.

The `update.sh` script will also run the linter and the unit tests.

The update process continues until the reviewer thinks the code is good enough to be submitted into the project. Then a "**LGTM**" (Looks Good To Me) is given and you can submit the code.

#### Code freeze period

Shortly before we make a new release a code freeze period will be announced on the development mailing list. During that code freeze no new features will be allowed to be submitted into the project codebase. During that time the focus is on testing and bug fixes.

In such a freeze, new features will added to the codebase after the release. The project owners should typically warn you that we are in a code freeze if there is any chance of you needing to submit a new feature during code freeze.