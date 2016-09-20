### Read Command Output & Status
```
#!/usr/bin/python

import subprocess

p = subprocess.Popen("date", stdout=subprocess.PIPE, shell=True)

# Communicate with date command i.e. read data from stdout & stderr, store in tuple
(output, err) = p.communicate()

# Wait for date to terminate. Get return returncode ##
p_status = p.wait()

print "Command output : ", output
print "Command exit status/return code : ", p_status

```

### Get Real Time Output
```
#!/usr/bin/python

import subprocess,sys

cmd = "top"

process = subprocess.Popen( cmd, stdout=subprocess.PIPE, shell=True)

while True:
        output = process.stdout.readline()
        if output == '' and process.poll() is not None:
            break
        if output:
            print output.strip()


```
