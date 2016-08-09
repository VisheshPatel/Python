### Template for printing sheet row by row

```
from openpyxl import load_workbook
wb = load_workbook('Book1.xlsx')
ws = wb.active
for row in ws.iter_rows():
   for cell in row:
     print cell.value
```

### Installing openpyxl Module

- Step 1 : Downloading Module tar file
`wget https://pypi.python.org/packages/25/69/7976ba24d2b532e96157623daa8de4bbcad23e0761b3062d5e38775577d5/openpyxl-2.4.0-b1.tar.gz`
- Step 2 : Untar it
`tar -xvf openpyxl-2.4.0-b1.tar.gz`
- step 3 : Installing it
`cd openpyxl-2.4.0-b1`
`./setup.py install`

### Other modules to parse excel sheets

- [Python Modules to parse Excels](http://www.python-excel.org/)
