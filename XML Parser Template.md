
```
import sys
import csv
try:
	# Use c implementation to speed-up parsing
  import xml.etree.cElementTree as ET
except ImportError:
	# Else use python one
  import xml.etree.ElementTree as ET
    
# create element tree object
tree = ET.parse(IPXACT_file) 

# get root element
root = tree.getroot()

# Iterate over all child under root
for child in root:
  print (child.tag, child.attrib, child.text)    
  
# Iterate like DFS over all child
for elem in root.iter():
  print(elem.tag, elem.attrib, elem.text)
  
# Iterate to specific tag
for elem in root.iter(tag='register'):
  print(elem.tag, elem.attrib, elem.text)  
```
