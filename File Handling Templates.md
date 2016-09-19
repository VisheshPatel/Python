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

### Normal Operations

```
#!/usr/bin/python

fo = open("foo.txt", "w+")      # Write & Read
fo.write( "Python is a great language.\nYeah its great!!\n");

# Close opend file
fo.close()
```
