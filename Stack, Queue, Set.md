
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
