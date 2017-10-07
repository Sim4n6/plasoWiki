### Fedora Core 25 and 26

To install plaso from the GIFT COPR you'll need to have dnf plugins installed:

```
sudo dnf install dnf-plugins-core
```

Add the [GIFT Cool Other Package Repo (COPR)](https://copr.fedorainfracloud.org/groups/g/gift/coprs/):

```
sudo dnf copr enable @gift/stable
```

Install plaso:
```
sudo apt-get install python-plaso plaso-tools
```