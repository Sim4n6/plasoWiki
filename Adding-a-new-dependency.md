There are several steps involved for a new dependency to plaso.

**TODO describe**
* update [Licenses dependencies](https://github.com/log2timeline/plaso/wiki/Licenses-dependencies)

## Checklist
If the answer on any of the questions below is no the dependency is not suitable for plaso. In that case see: [Alternatives](https://github.com/log2timeline/plaso/wiki/Adding-a-new-dependency#alternatives)

* Has the dependency a [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0) compatible license?

Code licensed under a GPL or BSD 4-clause cannot be integrated in a binary build, hence these licenses are deemed incompatible. Note that this could also apply to other source code licenses.

* Does the dependency support Linux, Mac OS X and Windows?

## Automated testing
The automated testing relies on having the dependencies available. We deliberately limit the usage of pip (or equivalent) in the automated testing scripts, mainly because pip distributed builds change continuously. We want to have a more stable set of dependencies on dependencies and limit the amount of troubleshooting due breakage caused by a dependency.

### Getting a dependency in l2tdevtools
Plaso relies on [l2tdevtools](https://github.com/log2timeline/l2tdevtools) to limit the amount of manual effort involved in maintaining dependencies.

**TODO: describe**

### Getting a dependency in GIFT
**TODO: describe**

### Getting a dependency in the [Google Drive Downloads](https://googledrive.com/host/0B30H7z4S52FleW5vUHBnblJfcjg/)
**TODO: describe**

## Source changes
**TODO: describe**

* update: [utils/check_dependencies.py](https://github.com/log2timeline/plaso/blob/master/utils/check_dependencies.py)
* update: appveyor.yml
* update: [.travis.yml](https://github.com/log2timeline/plaso/blob/master/.travis.yml)

## Documentation
**TODO: describe**

Update the following wiki pages:

* [Licenses dependencies](https://github.com/log2timeline/plaso/wiki/Licenses-dependencies)
* [Dependencies Fedora Core](https://github.com/log2timeline/plaso/wiki/Dependencies-Fedora-Core)
* [Dependencies Mac OS X](https://github.com/log2timeline/plaso/wiki/Dependencies-Mac-OS-X)
* [Dependencies Ubuntu](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu)
* [Dependencies Windows](https://github.com/log2timeline/plaso/wiki/Dependencies-Windows)

## Alternatives
**TODO: describe**