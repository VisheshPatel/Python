```
import threading
import time

sharedCounter = 0
lock = threading.Lock()
#lock = threading.RLock() # Re-entrant lock

def thread(arg1, arg2):
    global sharedCounter
    while True:
        # Always use exception handling with lock,
        # otherwise application stuck some cases
        lock.acquire()
        try:

            sharedCounter += arg2
            print "{} : sharedCounter = {:d}".format(arg1, sharedCounter)
        finally:
            # time.sleep(0.01)
            lock.release()

t1 = threading.Thread(target=thread, args=("Thread 1", 1))
t2 = threading.Thread(target=thread, args=("Thread 2", -1))


if __name__ == '__main__':
    t1.start()
    t2.start()
```


### Difference B/W Normal & Re-entrant Lock

```
lock = threading.Lock()
lock.acquire()
lock.acquire() # this will block

lock = threading.RLock()
lock.acquire()
lock.acquire() # this won't block
```
