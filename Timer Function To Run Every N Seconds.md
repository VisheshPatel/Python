```
def printit(i):
    i = i + 1
    print "Hello, World!"
    threading.Timer(5.0, printit, [i]).start()

printit(0)

# continue with the rest of your code

```
- This function schedule itself, Every 5 seconds
