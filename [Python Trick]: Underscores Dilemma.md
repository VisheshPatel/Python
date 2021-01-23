
- In Python variable & function names representing underscores have conventional as well as interpreter-enforced meaning.
- There could be following 5 underscore patterns that you might encounter:

1. Single Leading Underscore: `_var`
2. Single Trailing Underscore: `var_`
3. Double Leading Underscore: `__var`
4. Double Leading & Trailing Underscore: `__var__`
5. Single Underscore: `_`

## 1. Single Leading Underscore: "_var"

- A conventional meaning that indicate variable or method will be used internally. Something like, a tiny underscore warning that says: "Dude, this isn’t really meant to be a part of the
public interface of this class. Better to leave it alone."

- However, you must be careful while importing:

```Python
# my_module.py:

def external_func():
    return 23

def _internal_func():
    return 42
```

- Now, if you use a wildcard import to import all the names from the module:

```Python
>>> from my_module import *
>>> external_func()
23
>>> _internal_func()
NameError: "name '_internal_func' is not defined"
```

- Though, regular imports are not affected:

```Python
>>> import my_module
>>> my_module.external_func()
23
>>> my_module._internal_func()
42
```

## 2. Single Trailing Underscore: "var_"

- Used by convention to avoid naming conflicts with Python keywords:

```Python
>>> def make_object(name, class):
SyntaxError: "invalid syntax"
>>> def make_object(name, class_):
... pass
```

## 3. Double Leading Underscore: "__var"

- Triggers name mangling when used in a class context. Enforced by the Python interpreter:

```Python
class Test:
    def __init__(self):
        self.foo = 11
        self._bar = 23
        self.__baz = 23

>>> t = Test()
>>> print(t.foo)   
11 
>>> print(t._bar)     
23
>>> print(t.__baz) 
AttributeError: 'Test' object has no attribute '__baz'
```
- Interpreter enforced renaming:
```Python
>>> print(dir(t))    
['_Test__baz', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_bar', 'foo']
>>> print(t._Test__baz)
23
```
- Same goes for methods as well.

## 4. Double Leading and Trailing Underscore: `__var__`

- Indicates special methods are known as dunders i.e. `__init__`, `__call__`, etc  .
- It's better to stay away from using your own names with double leading and trailing underscore to avoid collisions with future changes to the Python.

## 5. Single Underscore: "_"

- Sometimes used as a name for temporary or insignificant variables. 
```Python
>>> for _ in range(5):
...     print('Hello, World.')
>>> car = ('red', 'auto', 12, 3812.4)
>>> color, _, _, mileage = car
```
- Also, it represents the result of the last expression in a Python REPL session.
```Python
>>> 20 + 3
23
>>> _
23
>>> list()
[]
>>> _.append(1)
>>> _.append(2)
>>> _.append(3)
>>> _
[1, 2, 3]
```

P.S.: Kindly ignore the mail if you know this already!
