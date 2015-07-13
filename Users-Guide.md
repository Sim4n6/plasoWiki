**This page is work in progress.**

For the current version of the documentation see: https://sites.google.com/a/kiddaland.net/plaso/usage

## How to get started

1. Determine which version of plaso is must suitable to your needs, for more information see [Releases and roadmap](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap)


## I know the good old Perl version

If you are one of those people that liked the old perl version of log2timeline but really would like to switch use all the nifty features of the Python version. Fear not, [here](https://github.com/log2timeline/plaso/wiki/Upgrading-From-0.x-Branch) is a guide to help you migrate.

## Installing plaso - the end-user edition
**This page is work in progress.**

### Unbuntu 14.04 LTS
First make sure your system is up to date:
```
sudo apt-get update
sudo apt-get upgrade
```

Add the [GIFT PPA](https://launchpad.net/~gift) and install plaso.
```
sudo add-apt-repository ppa:gift/stable
sudo apt-get update
sudo apt-get install plaso-1.3.0-1ppa1~trusty
```