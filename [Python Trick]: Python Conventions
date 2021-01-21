
- In other languages variable & function names representing underscores have conventional meaning.however in Python it has both conventional as well as enforced meaning by the Python interpreter
- Following 5 underscore patterns and naming conventions, and how they affect the behavior of your Python programs

    - Single Leading Underscore: `_var`
    - Single Trailing Underscore: `var_`
    - Double Leading Underscore: `__var`
    - Double Leading and Trailing Underscore: `__var__`
    - Single Underscore: `_`

1. Single Leading Underscore: “_var”

Summary: Naming convention indicating a name is meant for internal use. Generally not enforced by the Python interpreter (except in wildcard imports)
and meant as a hint to the programmer only

- Conventional meaning saying that variable or method will be used internally. This convention is defined in PEP 8, the most commonly used Python code style guide.
- Its like putting up a tiny underscore warning sign that says: “Hey, this isn’t really meant to be a part of the
public interface of this class. Best to leave it alone.”

- However, leading underscores do impact how names
get imported from modules. Imagine you had the following code in a
module called my_module:

```Python
# my_module.py:

def external_func():
    return 23

def _internal_func():
    return 42
```

- Now, if you use a wildcard import to import all the names from the module, Python will not import names with a leading underscore (unless the module defines an `__all__` list that overrides this behavior9):

```Python
>>> from my_module import *
>>> external_func()
23
>>> _internal_func()
NameError: "name '_internal_func' is not defined"
```

- By the way, wildcard imports should be avoided as they make it unclear which names are present in the namespace.10 It’s better to stick to regular imports for the sake of clarity. Unlike wildcard imports, regular imports are not affected by the leading single underscore naming
convention:

```Python
>>> import my_module
>>> my_module.external_func()
23
>>> my_module._internal_func()
42
```

2. Single Trailing Underscore: “var_”

Summary: Used by convention to
avoid naming conflicts with Python keywords.

- Sometimes the most fitting name for a variable is already taken by a keyword in the Python language. Therefore, names like class or def cannot be used as variable names in Python. In this case, you can
append a single underscore to break the naming conflict:

```Python
>>> def make_object(name, class):
SyntaxError: "invalid syntax"
>>> def make_object(name, class_):
... pass
```

3. Double Leading Underscore: “__var”

Summary: Triggers name mangling when used in a class context. Enforced by the Python interpreter

- A double underscore prefix causes the Python interpreter to rewrite the attribute name in order to avoid naming conflicts in subclasses. This is also called name mangling—the interpreter changes the name of the variable in a way that makes it harder to create collisions when the class is extended later.

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

- 

```Python
>>> print(dir(t))    
['_Test__baz', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_bar', 'foo']
```

```Python
>>> print(t._Test__baz)
23
```
- Same goes for methods as well.

4. Double Leading and Trailing Underscore: `__var__`

Summary: Indicates special methods defined by the Python language. Avoid
this naming scheme for your own attributes.

- Variables surrounded by a double underscore prefix and postfix does not mangled. But when it comes to methods, it has special meaning. Such methods are known as dunders I.e. `__init__`, `__call__`, etc  .
- it’s best to stay away from using names that start and end with double underscores in your own programs to avoid collisions with future changes to the Python language.

5. Single Underscore: “_”

Summary: Sometimes used as a name for temporary or insignificant variables (“don’t care”). Also, it represents the result of the last expression in a Python REPL session.

- Per convention, a single stand-alone underscore is sometimes used as a name to indicate that a variable is temporary or insignificant.
For example, in the following loop we don’t need access to the running index and we can use “_” to indicate that it is just a temporary value:
```Python
>>> for _ in range(32):
... print('Hello, World.')
```
You can also use single underscores in unpacking expressions as a “don’t care” variable to ignore particular values.

```Python
>>> car = ('red', 'auto', 12, 3812.4)
>>> color, _, _, mileage = car
```
Besides its use as a temporary variable, “_” is a special variable in most Python REPLs that represents the result of the last expression evaluated by the interpreter.

```Python
>>> 20 + 3
23
>>> _
23
>>> print(_)
23
>>> list()
[]
>>> _.append(1)
>>> _.append(2)
>>> _.append(3)
>>> _
[1, 2, 3]
```
