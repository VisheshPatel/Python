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

p = subprocess.Popen(cmd, shell=True, stderr=subprocess.PIPE)

while True:
        out = p.stderr.read(1)
        if out == '' and p.poll() != None:
                break
        if out != '':
                sys.stdout.write(out)
                sys.stdout.flush()

```
