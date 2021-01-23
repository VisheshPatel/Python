## [Python Trick]: Managing context using "with" statement

- You might have used `with` statement while working with files as:

```python
with open("myfile.txt") as file:
  for line in file:
    print(line)
```

- This is recommended way of opening files because it ensures that open file descriptors are closed automatically after program execution leaves the context of the with statement. 
- But have you ever wondered, **How is it works internally?**
- Well, if not then here you go, internally, the above code sample translates to something like this:

```python
file = open("myfile.txt")
try:
    for line in file:
        print(line)
finally:
    file.close()
```

- This is something similar to **R**esource **A**cquisition **I**s **I**nitialization i.e. RAII idiom in C++.
- You can employ similar technique in python wherever you need resources for time-being like mutex lock & unlock.
- Now the question is how you can make use of `with` statement with custome data types!
- Its easy! All you need to do is to add dunder-methods i.e. `__enter__` and `__exit__` as follow:

```python
class ManagedFile:
    def __init__(self, name):
        self.name = name
    def __enter__(self):
        self.file = open(self.name)
        return self.file
    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

with ManagedFile("myfile.txt") as file:
    for line in file:
        print(line)
```

Have A Happy Learning...!

P.S.: Kindly ignore the mail if you know this already!
