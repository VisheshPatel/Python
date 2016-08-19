### Reading File Line by Line

```
#!/usr/bin/python

FILE_NAME = "xyz.txt"

with open(FILE_NAME) as f:
        for line in f:
                print(line)
```
