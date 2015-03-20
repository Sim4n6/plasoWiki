Plaso comes in 2 different forms of releases:

* a packaged release; found on the [Releases page](https://github.com/log2timeline/plaso/releases)
* a development release; found in the [git repository](https://github.com/log2timeline/plaso)

**Note that the development release is for development, expect frequent updates and potential breakage.**

If you do not plan to develop or live on the edge, regarding plaso, we highly recommend sticking with the packaged release. We will try to provide two packaged releases per year, a "summer" and "winter" release (depending on your location), but occasionally we will also do preview and release candidate packaged releases.

## Roadmap
The following sections contain a rough outline of the larger items on the roadmap. For more detailed information see: [Plaso - Roadmap and Assignment](http://goo.gl/cRjA7y)

**TODO describe larger ideas below.**

### Version 1.2.1

* Event Log event messages support
* initial hasher support
* improved image export
* Parsers
  * Chrome preferences parser
  * improved MSIECF parser
* Windows Registry plugins
  * WinReg Timezone Plugin
* changes due to dfVFS using more strict caching strategy
* changes to handling of compressed files and archives
* added signature-based parser pre-filtering
* split off l2tdevtools
* clean-up and fixes
  * parser chain
  * parser mediator

### Version 1.3.0

* Plaso as a module; Clean up and rewrite of the engine code (the parts that were not touched previously); Stabilize an API
* [storage redesign](https://github.com/log2timeline/plaso/issues/102)
* [winreg: clean up and improve](https://github.com/log2timeline/plaso/issues/145)
* Parsers
  * job file parser - add format improvements

### Mid/Long term

* Artifact support
* Migration to Python 3
  * requires other dependencies being Python 3 compatible
  * Migration to construct 3
* Improved handling recovered (deleted) data
* Plaso as a service
* Sandboxing the workers

## Packaged release history
Version | Name | Release date | Comments
--- | --- | --- | ---
1.0.0 | | December 2012 | [Blog post](http://blog.kiddaland.net/2012/12/first-alpha-release-of-log2timeline.html)
1.0.1 | | April 2013 | [Blog post](http://blog.kiddaland.net/2013/04/flowers-blossoming-trees-and-new-plaso.html)
1.0.2 | Spooky edition | October 2013 | [Blog post](http://blog.kiddaland.net/2013/10/halloween-brings-with-it-riding-witches.html)
1.1.0 | SuperBark edition | June 2014 | [Blog post](http://blog.kiddaland.net/2014/06/what-is-one-to-say-about-june-time-of.html)
1.2.0 | Griswold edition | December 2014 | [Blog post](http://blog.kiddaland.net/2014/12/hey-kids-i-heard-on-news-that-airline.html)