```
import thread
import time

def print_time(threadName, delay):
    while True:
        print "Thread Running"
        time.sleep(delay)

try:
    thread.start_new_thread(print_time, ("Thread 1", 2, ))
except:
    print "Error: unable to start thread"

while True:
    pass
```
