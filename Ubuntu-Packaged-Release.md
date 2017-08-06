### SANS Investigative Forensic Toolkit (SIFT) Workstation
SIFT workstation version 3 adds the [GIFT PPA](https://launchpad.net/~gift) stable track. All you need to do get the most recent stable release of Plaso is:
```
sudo apt-get update
sudo apt-get install python-plaso
```

### Ubuntu 14.04 LTS

To install plaso you'll need to have Ubuntu universe enabled:

```
sudo add-apt-repository universe
sudo apt-get update
```

Not necessary but we recommend that your installation is up to date:

```
sudo apt-get upgrade
```

Add the [GIFT PPA](https://launchpad.net/~gift):
```
sudo add-apt-repository ppa:gift/stable
```

Update and install plaso:
```
sudo apt-get update
sudo apt-get install plaso-tools python-plaso
```

### Upgrading from version 1.2 to 1.3

One of the dependencies was renamed causing conflicts when upgrading from stable version 1.2 to version 1.3. In order to fix that conflict the following commands need to be run:
```
sudo apt-get update
sudo apt-get remove binplist python-plaso
sudo apt-get install python-plaso
```

