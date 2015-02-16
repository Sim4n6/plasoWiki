This page contains detailed instructions on how to build and install dependencies on Fedora Core. Some of these instructions should also work on Fedora Core like systems like RHEL or OpenSuze.

There are multiple ways to install the dependencies on Fedora Core:

* Using the [log2timeline devtools](https://github.com/log2timeline/devtools) to batch build most of the dependencies;
* Manual build of the dependencies.

## Batch build
**TODO migrate this to log2timeline devtools**

First set up a working build environment.

**TODO: describe.**

To have the build_dependencies script build the rpm package files run:
```
C:\Python27\python.exe utils\build_dependencies.py rpm
```

## Manual build
It is impossible for us to support all flavors of Fedora Core out there, so if you want smooth sailing, we recommend sticking with the supported version or live with the fact that a manual build of the dependencies can be a tedious task.

For ease of maintenance the following instructions use as much rpm package files as possible. Note that the resulting rpm files are not intended for public redistribution.

Alternative installation methods like installing directly from source, using easy_install or pip are not recommended because when not maintained correctly they can mess up your setup more easily than using rpm packages.

First create a build root directory:
```
mkdir plaso-build/
```

Next make sure your installation is up to date:
```
sudo yum update
```
