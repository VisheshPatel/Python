```
def printit():
    threading.Timer(5.0, printit).start()
    print "Hello, World!"

printit()

# continue with the rest of your code

```
- This function schedule itself, Every 5 seconds
