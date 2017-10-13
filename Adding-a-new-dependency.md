There are several steps involved for getting a new dependency added to plaso.

## Before you begin checklist
If the answer on any of the questions below is no the dependency is not suitable for plaso. In that case see: [Alternatives](https://github.com/log2timeline/plaso/wiki/Adding-a-new-dependency#alternatives)

* Has the dependency a [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0) compatible license?

Code licensed under a GPL, AGPL or BSD 4-clause cannot be integrated in a binary build, hence these licenses are deemed incompatible. Note that this could also apply to other source code licenses.

* Does the dependency support Linux, Mac OS X and Windows?

## Automated testing
The automated testing relies on having the dependencies available. We deliberately limit the usage of pip (or equivalent) in the automated testing scripts, mainly because pip distributed builds change continuously. We want to have a more stable set of dependencies on dependencies and limit the amount of troubleshooting due breakage caused by a dependency.

### Getting a dependency in l2tdevtools
Plaso uses [l2tdevtools](https://github.com/log2timeline/l2tdevtools) to limit the amount of manual effort required in maintaining dependencies.

If the build process of the dependency is similar enough what is currently supported then adding a new dependency should be relative straight forward by adding it to [data/projects.ini](https://github.com/log2timeline/l2tdevtools/blob/master/data/projects.ini). If not reach out to discuss how we can get support into l2tdevtools for the specific dependency.

### Getting a dependency in GIFT
Once the dependency has been added to l2tdevtools it can be added to the [GIFT PPA](https://launchpad.net/~gift). Ask one of the PPA maintainers to upload your package.

**Note for PPA maintainers upload new packages always to the [testing track](https://launchpad.net/~gift/+archive/ubuntu/testing) first.**

### Getting a dependency in l2tbinaries
Once the dependency has been added to l2tdevtools it can be added to [l2tbinaries](https://github.com/log2timeline/l2tbinaries). Ask one of the maintainers to upload your package.

**Notes for maintainers:** https://github.com/log2timeline/l2tdocs/blob/master/process/l2tbinaries.md

## Source changes
**TODO: describe**

* update: [plaso/dependencies.py](https://github.com/log2timeline/plaso/blob/master/plaso/dependencies.py) and run ./utils/update_dependencies.py
* update: [appveyor.yml](https://github.com/log2timeline/plaso/blob/master/appveyor.yml) if needed; make sure the dependency is available via [l2tbinaries](https://github.com/log2timeline/l2tbinaries) and part of the l2tdevtools [plaso dependencies preset](https://github.com/log2timeline/l2tdevtools/blob/master/data/presets.ini)

Files no longer needed to update manually:

* update: [.tox.ini](https://github.com/log2timeline/plaso/blob/master/.tox.ini); updated by ./utils/update_dependencies.py
* update: [.travis.yml](https://github.com/log2timeline/plaso/blob/master/.travis.yml); update [config/linux/install_gift_and_dependencies.sh](https://github.com/log2timeline/plaso/blob/master/config/linux/install_gift_and_dependencies.sh) instead
* update: [config/dpkg/control](https://github.com/log2timeline/plaso/blob/master/config/dpkg/control); updated by ./utils/update_dependencies.py
* update: [config/linux/install_gift_and_dependencies.sh](https://github.com/log2timeline/plaso/blob/master/config/linux/install_gift_and_dependencies.sh); updated by ./utils/update_dependencies.py
* update: [setup.cfg](https://github.com/log2timeline/plaso/blob/master/setup.cfg); updated by ./utils/update_dependencies.py

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