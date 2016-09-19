### Reading File Line by Line

```
#!/usr/bin/python

FILE = "xyz.txt"

with open(FILE) as f:
        for line in f:
                print(line)
                print(f.next())        
                f.writelines("This is test line")
```
