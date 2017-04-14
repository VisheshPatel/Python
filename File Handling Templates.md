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

fo = open("foo.txt", "wb+")      # Write & Read


print "Name of the file: ", fo.name
print "Closed or not : ", fo.closed
print "Opening mode : ", fo.mode
print "Softspace flag : ", fo.softspace

# Check current position
position = fo.tell();
print "Current file position : ", position

# Reposition pointer at the beginning once again
position = fo.seek(0, 0);
str = fo.read(20);
print "Again read String is : ", str

# Write
fo.write( "This is test line X");

fo.close()

```
