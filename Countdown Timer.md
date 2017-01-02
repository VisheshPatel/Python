```
#!/usr/bin/python

import time,sys

def countdown_seconds(t):
    while t:
        mins, secs = divmod(t, 60)
        timeformat = '{:02d}:{:02d}'.format(mins, secs)
        sys.stdout.write("\r"+timeformat)
        sys.stdout.flush()
        time.sleep(1)
        t -= 1

    print "\nGoodbye!"


countdown_seconds(65)

```
