
### Iterating List
```
list = [3,4,5,6]

for index, value in enumerate(list):
        print index, value
```

### Iterating Tuple
```
tuple = [(1,2), (3,4), (5,6)]

for index, (a, b) in enumerate(tuple):
        print "Index = ", index, "First", a, "then", b
```
### Iterating Dictionary
```
dict = {'x': 1, 'y': 2, 'z': 3}

for key,value in dict.items():
                print key, value
```

### Searching in list
```
list = [3,4,5,6]

if 4 in list:
	print("Present")
```


### Searching in List of Tuple
```
tupleList = [(1,2), (3,4), (5,6)]

if [item for item in tupleList if item[0] == 1]:
	print("Item Found")
```

### Searching in Dictionary
```
dict = {'x': 1, 'y': 2, 'z': 3}

key = 'x'
if key in dict.keys(): print("dict contains key", key)

value = 2
if value in dict.values(): print("dict contains key", value)
```
