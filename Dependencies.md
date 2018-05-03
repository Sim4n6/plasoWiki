This page contains detailed instructions on how to build and install dependencies.

There are multiple ways to install the dependencies:

* Using prepackaged versions of the dependencies;
* Using the [log2timeline devtools](https://github.com/log2timeline/devtools) to batch build most of the dependencies;
* Manual build of the dependencies.

## Prepackaged dependencies

### Fedora Core

**Note that the instructions in this page assume you are running on Fedora Core 25. Installing packages from the copr on other versions and/or distributions is not recommended.**

The [GIFT copr](https://copr.fedorainfracloud.org/groups/g/gift/coprs/), contains the necessary packages for running plaso. The GIFT copr provides the following tracks:

* stable; track intended for the "packaged release" of plaso and dependencies;
* dev; track intended for the "development release" of plaso;
* testing; track intended for testing newly created packages.

For development we recommend using the dev track. To add it to your dnf configuration run:

```
sudo dnf install dnf-plugins-core
sudo dnf copr enable @gift/dev
```

To install the dependencies run:

```
sh config/linux/gift_copr_install.sh include-development include-test
```

For troubleshooting crashes it is recommended to install the following debug symbol packages as well:

```
sh config/linux/gift_copr_install.sh include-debug
```

## Batch build

**Note that the batch build script is currently still work in progress, but it will build most of the dependencies.**

Set up the [l2tdevtools build script](https://github.com/log2timeline/l2tdevtools/wiki/Build-script) and run:
```
PYTHONPATH=. python tools/build.py ${BUILD_TARGET}
```

Where `${BUILD_TARGET}` is the build target for your configuration. If you are unable to find the proper build target we do not recommend using this installation method.

Successfully built packages will be stored in the build directory, which is `build` by default. You can use your preferred installation method to install them.
