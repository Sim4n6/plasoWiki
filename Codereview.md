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

We continuously try to improve the code base, including making things and easier and quicker to write which sometimes means that the way you just learned might already superseded by another. We try to keep the documentation up to date but this sometimes be after you ran into an issue.

First time contributors may come across the fact that the code review process actually takes quite a long time, with lots of back and forth comments. You may think that you are wasting the core developers time, but rest assured you are not. We look at this as an investment of building up good solid code contributors. We would like to make sure our contributors understand the code and the style guide and will make suggestions to the contributor to fix what we think needs improving. Despite spending potentially more time to begin with to get code submitted into the project we believe this investment in code review will result in better code submissions and increased proficiency of the contributor.

Therefore we would like to ask people to hang on, to get through the code review process and try to learn something while going through it. Rest assured, it will get easier next time and even easier the time after that, and before you know it you can contribute code to the project with little to no comments.

And if things are unclear, don't hesitate to ask. The developer mailing list is: log2timeline-dev@googlegroups.com

### How it Works

Disclaimer: this process is geared towards those that do their development on a platform that supports bash scripts (as in *NIX and Mac OS X). For those that do not have that luxory, you may need to use alternative methods (as in more manual approach).

 * From your local checkout make your changes, do **not do** a `git commit`
 * Write both the code and accompanying unit tests
 * Test your code, preferably running both the unit tests and test it against real data
 * When you are ready for the code to be reviewed follow the next steps.

#### Uploading code to Code Review Site

Use the `review.sh` script:

    ./utils/review.sh [--nobrowser] email_of_a_reviewer

Where the "*email_of_a_reviewer*" can be anyone from the plaso [owners](https://github.com/orgs/log2timeline/teams/owners).

The upload script uses OAuth to authenticate so you need to have a browser that is signed in using the developers account and give the app permissions to your account (needs to be a Google account).

This will invoke few things; running pylint to catch obvious style guide issues, run all local tests, etc. If all of these things run successfully the script will ask you for a description of the change. The description should refer to the relevant issue ticket you are working on, eg:

    Added serializers profiler #120

Where the "#120" is a reference to issue nr. 120 on the github site. After the description has been entered in the code will be uploaded to rietveld for review.

If you are developing the code from a computer that does not have a browser installed, or you are accessing the dev machine remotely you need to supply the "*--nobrowser*" parameter and then visit the following site on a computer that has a browser:

    https://codereview.appspot.com/get-access-token

This will create an OAuth token that you can copy+paste to the terminal window.

You should see something like this if everything goes well:

    Issue created: URL: http://codereview.appspot.com/6811077

That is the tool should print the URL of your code change on rietveld showing your submission number. If necessary you can go to the review page, click edit and update the reviewers or description.

This will trigger an email sent out to the developer mailing list, notifying people that there is a code review pending and it will show up in the reviewers queue on the rietveld site.

After the code is uploaded to rietveld, please go back into github and update the issue indicating that you've submitted code for review. That makes it simpler to track the status of the various issues.

#### Working Through Code Review

During the code review process you'll be asked to change few things, that is the reviewer will add comments. Please follow the following guideline during the code review process:

 * Answer **ALL** comments made in the code review, even if it is only an ACK or "Done".
   * It is also necessary to publish the comments, otherwise the reviewer doesn't see the answers.
   * On the codereview site hit "m" for "Publish+Mail Comments" so that the review gets updated alongside the newly updated code.
 * Make the necessary changes to the code, as suggested by the reviewer.
 * Make sure you have not checked in the changes locally (as in not executed `git commit`").

When all code changes have been completed and you are ready for another round execute:

    ./utils/update.sh [--nobrowser]

This will invoke similar process as before (running linter, tests, etc).

This process continues until the reviewer thinks the code is good enough to be submitted into the project. Then a "**LGTM**" (Looks Good To Me) is given and you can submit the code.

**DO NOT SUBMIT** code to the project before a LGTM has been sent in the code review site. All code submitted without an explicit LGTM will be revoked and rolled back.

#### Submitting code

At this point the code is ready, has been approved for submission and everything should be good to go.

At this point it is good to double check that there hasn't been any code submitted into the project again that may break your code. A good rule of thumb is to:

    git stash
    git pull
    git stash pop

If there are changes applied during the `git pull` command you may want to re-run all of your tests to make sure things are still working as intended.

In the case where there are merge conflicts git will warn you and you need to manually fix them before continuing.

Given that everything is still working you can now submit the code:

    ./utils/submit.sh [--nobrowser]

This will run all the previous steps again, such as checking linter and tests. If all succeeds the script then does a `git commit` and a `git push` to push out the changes. There should be no need to do anything else on the git side.

The next step is to manually close the Rietveld code review (a picture of a X in the upper left corner). If the ticket is not closed it will stay in the reviewer queue.

There are also other things that happen once the code is submitted to the codebase, a new test run is executed on travis and code coverage is added to coveralls, see:

 * [Travis] (https://travis-ci.org/log2timeline/plaso)
 * [Coverage] (https://coveralls.io/r/log2timeline/plaso)
 * [AppVeyor] (https://ci.appveyor.com/project/joachimmetz/plaso)

If for some reasons the code breaks on travis yet works on the developer workstation that may be an indication that some dependencies are missing or the developer made some assumptions that do not apply on other machines (such as explicit path declaration to reach out to files on their workstation, etc).

If the code submitted breaks travis, please create another CL (changelist) that fixes the issue. All the fixes need to go through code review, so don't push out a change without having someone review the change. Fixes that break travis should go through code review pretty quickly.

#### Caveats to Submit

Shortly before we make a new release a code freeze period will be announced on the development mailing list. During that code freeze no new features will be allowed to be submitted into the project codebase. During that time the focus is on testing and bug fixes.

In such a freeze, new features will added to the codebase after the release.