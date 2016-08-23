```
string = "this is string example....sdfasdfsa!!!"

pattern = "is"
```
### With Condition
```
if pattern in string:
	print("Found Sub-Word")
```

### Find Pattern Between start & end 
```
print("string.find(pattern)", string.find(pattern))

print("string.find(pattern,0,len(string))", string.find(pattern,0,len(string)))
```

### Split String with Delimiter
```
print(string.split(' '))
```

### Get the Index of Pattern
```
print(string.index("example"))
```

### Replace pattern
```
print(string.replace("string", "string immutable"))
```

### Centralize & Fill with char
```
print(string.center(50,'*'))
```

### Join Multiple String
```
s = "-";
seq = ("a", "b", "c"); 
print (s.join( seq ))
```
