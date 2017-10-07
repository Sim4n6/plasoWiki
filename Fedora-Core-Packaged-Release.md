### Fedora Core 25 and 26

To install plaso from the GIFT Cool Other Package Repo (COPR) you'll need to have dnf plugins installed:

```
sudo dnf install dnf-plugins-core
```

Add the [GIFT COPR](https://copr.fedorainfracloud.org/groups/g/gift/coprs/):

```
sudo dnf copr enable @gift/stable
```

Install plaso:
```
sudo apt-get install python-plaso plaso-tools
```

### Fedora Core 27

Not supported at this time.
