Plaso comes in 2 different forms of releases:

* a packaged release; found on the [releases page](https://github.com/log2timeline/plaso/releases)
* a development release; found in the [git repository](https://github.com/log2timeline/plaso)

**Note that the development release is for development, expect frequent updates and potential breakage.**

If you do not plan to develop or live on the edge, regarding plaso, we highly recommend sticking with the packaged release. We will try to provide two packaged releases per year, a "summer" and "winter" release (depending on your location), but occasionally we will also do preview and release candidate packaged releases.

## Roadmap
The following sections contain a rough outline of the larger items on the roadmap. For more detailed information see: [Plaso - Roadmap and Assignment](http://goo.gl/cRjA7y)

* [Artifact support](https://github.com/log2timeline/plaso/issues/155)
* Refactors
  * storage
    * redesign how event objects are stored
    * add support for event groups
    * add support for events without a date and time value
  * analysis plugins
  * front-end, CLI, tools
  * output modules
  * text parser rewrite/optimization
* Improve file system support
  * [dfVFS](https://github.com/log2timeline/dfvfs/wiki/Roadmap)
  * $MFT, $UsnJrnl parsing
* Multi volume support
* Migration to Python 3
  * requires other dependencies being Python 3 compatible
  * Migration to construct 3
* Parsers
  * [add more parsers](http://goo.gl/cRjA7y)
  * improve existing parsers
    * job file parser - add format improvements
  * deprecate stat object in favour of file entry attributes
  * Add Windows 10 Prefetch support (pyscca)
* Add analysis plugins
  * NSRL Server
* Collection
  * Improve collection filters
* Hashing
  * Do NSRL matching prior to event extraction
  * Use an event database to shortcut file processing
* Deployment
  * Plaso as a module; Clean up and rewrite of the engine code (the parts that were not touched previously); Stabilize an API
  * Sandboxing the workers
  * Plaso as a service
  * Cross-system distributed plaso workers (RPC)
  * [storage redesign](https://github.com/log2timeline/plaso/issues/102)
* [Windows Registry support improvements](https://github.com/log2timeline/plaso/issues/145)
* Handling recovered (deleted) data

## Changes in development release
Changes in the version 1.2.1 development release:

* Core
  * added signature-based parser pre-filtering
  * initial hasher support
  * Windows Event Log event messages support
  * changes due to dfVFS using more strict caching strategy
  * changes to handling of compressed files and archives
* Parsers
  * Chrome preferences parser
  * improved MSIECF parser
  * Added rp.log parser
* ESE database file formats
  * Windows 8 File History
  * long value support
* Windows Registry plugins
  * WinReg Timezone Plugin
  * AppCompatCache Windows 10 support
* Output
  * improved TimeSketch integration
* Tools
  * improved image export
* Analysis plugins
  * Virustotal
* clean-up and fixes
  * parser chain
  * parser mediator
  * split off build and update dependency utility scripts to a separate project
  * various refactors

## Packaged release history
Version | Name | Release date | Comments
--- | --- | --- | ---
1.0.0 | | December 2012 | [Blog post](http://blog.kiddaland.net/2012/12/first-alpha-release-of-log2timeline.html)
1.0.1 | | April 2013 | [Blog post](http://blog.kiddaland.net/2013/04/flowers-blossoming-trees-and-new-plaso.html)
1.0.2 | Spooky edition | October 2013 | [Blog post](http://blog.kiddaland.net/2013/10/halloween-brings-with-it-riding-witches.html)
1.1.0 | SuperBark edition | June 2014 | [Blog post](http://blog.kiddaland.net/2014/06/what-is-one-to-say-about-june-time-of.html)
1.2.0 | Griswold edition | December 2014 | [Blog post](http://blog.kiddaland.net/2014/12/hey-kids-i-heard-on-news-that-airline.html)
1.3.0 | | Planned June 2015 | 