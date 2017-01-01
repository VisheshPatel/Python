### Creating Thread

```
import threading
import time


def print_time(threadName, delay):
    while True:
        print "Thread Running"
        time.sleep(delay)

try:
    t1 = threading.Thread(target=print_time, args=("Thread 1", 1))
    t1.start()
except:
    print "Error: unable to start thread"

while True:
    pass
```
