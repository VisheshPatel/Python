```
import threading
import time

sharedCounter = 0
semaphore = threading.BoundedSemaphore()

def thread(arg1, arg2):
    global sharedCounter
    while True:
        # Always use exception handling with lock,
        # otherwise application stuck some cases
        semaphore.acquire()  # decrements the counter
        try:

            sharedCounter += arg2
            print "{} : sharedCounter = {:d}".format(arg1, sharedCounter)
        finally:
            time.sleep(0.01)
            semaphore.release()  # increments the counter

t1 = threading.Thread(target=thread, args=("Thread 1", 1))
t2 = threading.Thread(target=thread, args=("Thread 2", -1))


if __name__ == '__main__':
    t1.start()
    t2.start()
```
