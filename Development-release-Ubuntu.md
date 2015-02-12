Checkout the plaso source from the git repo:
```
git clone https://github.com/log2timeline/plaso.git
```

To be able to run the plaso [development release](https://github.com/log2timeline/plaso/wiki/Releases-and-roadmap) on Ubuntu or equivalent you'll have to have installed the [dependencies](https://github.com/log2timeline/plaso/wiki/Dependencies---Ubuntu).

Check if you have all the dependencies installed and have the right minimum version:
```
python utils/check_dependencies.py
```

**Note that some dependencies are actively under development and can be frequently updated, therefore we recommend checking the status of the dependencies regularly.**

## Update frequently
If you really want to run the development release, aka "Bleeding Edge", make sure to update frequently.

To update plaso:
```
git pull origin master
```

If you are using a "github fork" make sure your remote settings are correct:
```
git remote -v
origin	https://github.com/log2timeline/plaso (fetch)
origin	https://github.com/log2timeline/plaso (push)
```

**TODO: add note and link to devtools about maintaining dependencies.**

## Development tools
### pylint
**TODO: describe**
