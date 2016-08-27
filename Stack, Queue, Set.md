
### List as Stack

```
stack = []

stack.append(3)	# Works As a Push Operation, Add at right side(that is bottom)
stack.append(2)
stack.append(1)

print(stack.pop())	# Pop Element From Last(that is bottom)
print(stack.pop())	
print(stack.pop())	

if stack == []:		# OR if not stack:
	print("Stack is Empty")
```

### List as Queue

```
queue = []

queue.insert(0,3)	# Works As a Push Operation, Add at Left Side(that is top)
queue.insert(0,2)
queue.insert(0,1)

print(queue.pop())	# Pop Element From Last(that is bottom)
print(queue.pop())	
print(queue.pop())	

if queue == []:		# OR if not queue:
	print("Queue is Empty")
```

### set : Unordered collections of unique elements

> Declaration

```
Engineers = set(["vishal","vijay","vivek","vishal","vishnu"])	

print(Engineers)						# Will Print {'vijay', 'vishal', 'vivek', 'vishnu'} Only Distinct Elements
```
> Union

```
Programmers = set(["vishal","vijay"])	
Managers = set(["vivek","vaishna"])

Employees = Engineers | Programmers | Managers			# union
print(Employees)						# Will Print {'vijay', 'vishal', 'vivek', 'vishnu'}
```

> Intersection

```
Engineering_Management = Engineers & Managers            	# intersection
print(Engineering_Management)					# Will Print {'vivek'}
```

> Difference

```
Fulltime_Management = Managers - Engineers - Programmers 	# difference
print(Fulltime_Management)					# Will Print {'vaishna'}
```

> Add Element

```
Engineers.add("vairagi")                                 	# add element
print(Engineers)						# Will Print {'vishal', 'vishnu', 'vijay', 'vivek', 'vairagi'}
```
