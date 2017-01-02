```
#!/usr/bin/python

import inspect

def PrintFrame(msg):
        callerframerecord = inspect.stack()[1]    # 0 represents this line
                                                  # 1 represents line at caller
        frame = callerframerecord[0]
        info = inspect.getframeinfo(frame)

        print info.filename,":",info.lineno,":",info.function,":",msg

def Main():
  PrintFrame("Error in this line")                              # for this line

Main()

```
