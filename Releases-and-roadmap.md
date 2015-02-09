Plaso comes in 2 different forms of releases:

* a packaged release; found on the [Releases page](https://github.com/log2timeline/plaso/releases)
* a development release; found in the [git repository](https://github.com/log2timeline/plaso)

**Note that the development release is for development, expect frequent updates and potential breakage.**

We try to provide two packaged releases per year, a "summer" and "winter" release, but occasionally we will also do preview and release candidate packaged releases.

## Roadmap
A rough outline of the larger items on the roadmap:

### Version 1.2.1

* Plaso as a module; Clean up and rewrite of the engine code (the parts that were not touched in version 1.1.0); Stabilize an API
* dfVFS
  * Migration to SleuthKit 4.2 (assumed the new version is released)
* Storage
  * Add support for relocatable path specs
  * Add support to keep a protected copy of the decryption information for e.g. BitLocker
* Overhaul of winreg and plugins
  * remove Registry type
  * merge key and value plugins

### Mid/Long term

* Event Log event messages support
* Artifact support
* Migration to Python 3
  * requires other dependencies being Python 3 compatible
  * Migration to construct 3
* Improved handling recovered (deleted) data
* Plaso as a service
* Sandboxing the workers

Also see: [Plaso - Roadmap and Assignment](ttp://goo.gl/cRjA7y)

## Packaged release history
Version | Name | Release date | Comments
--- | --- | --- | ---
1.0.0 | | December 2012 | [Blog post](http://blog.kiddaland.net/2012/12/first-alpha-release-of-log2timeline.html)
1.0.1 | | April 2013 | [Blog post](http://blog.kiddaland.net/2013/04/flowers-blossoming-trees-and-new-plaso.html)
1.0.2 | Spooky edition | October 2013 | [Blog post](http://blog.kiddaland.net/2013/10/halloween-brings-with-it-riding-witches.html)
1.1.0 | SuperBark edition | June 2014 | [Blog post](http://blog.kiddaland.net/2014/06/what-is-one-to-say-about-june-time-of.html)
1.2.0 | Griswold edition | December 2014 | [Blog post](http://blog.kiddaland.net/2014/12/hey-kids-i-heard-on-news-that-airline.html)