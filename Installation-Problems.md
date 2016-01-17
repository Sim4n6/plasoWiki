## log2timeline failing dependencies check
When I run log2timeline it warns that certain dependencies are missing e.g.
```
Checking availability and versions of plaso dependencies.
[FAILURE]       missing: pyewf.
```

## I get strange errors that mention pyparsing.
This is common on Apple OSX, as that platforms bundles its own version of pyparsing, that is usually older than the version required by Plaso. Fix this by using the special wrapper scripts (log2timeline**.sh**, et. al.), or if you don't want to do that, manipulate PYTHONPATH so that the newer version is loaded. This is detailed on the OSX development page: https://github.com/log2timeline/plaso/wiki/Development-release-Mac-OS-X

**TODO: add more text**