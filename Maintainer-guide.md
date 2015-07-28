**TODO: add more text**

## Readthedocs.org
The plaso documentation on [readthedocs.org](https://readthedocs.org/projects/plaso/) is mirrored off the [plaso wiki](https://github.com/log2timeline/plaso/wiki). The wiki git repo does not have the same webhooks as the plaso source git repo and thus we rely on a manual build trigger in the [merge_submit script](https://github.com/log2timeline/plaso/blob/master/utils/merge_submit.sh) to refresh the documentation.

The build of the [plaso-api documentation](https://readthedocs.org/projects/plaso-api/) is triggered by the webhook of the plaso source git repo.

### Markdown compatibility
```
[description](URL)
```
Having a space between `]` and `(` breaks on readthedocs.

## Mailing list
Maintainers mailing list: log2timeline-maintainers@googlegroups.com