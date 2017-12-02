Notes on how to use the tagging analysis plugin.

## Creating the tagging file

A tagging-file.txt is an UTF-8 encoded text file that contains tagging expressions.

## Running plaso

First run log2timeline to extract events:
```
log2timeline.py timeline.plaso image.raw
```

Next run psort to tag events:
```
psort.py --analysis tagging --tagging-file tagging-file.txt timeline.plaso
```