## [Python Trick]: Decorator

### What is decorator?

- Decorators define reusable building blocks you can apply to function/method(i.e. a callable precisely) to modify its behavior without permanently modifying the original function/method.

```python
def decorator_example(original_func):
    print("Hello")
    return original_func

@decorator_example
def world():
    print("World")

world()
```
- Output
```
Hello
World
```

### How it works?

- There is nothing complicated, if you can think functions as object i.e. functions can be: 
    - Assigned to variables,
    - Passed to another function,
    - And returned from other functions

```python
def decorator_example(original_func):
    print("Hello")
    return original_func

def world():
    print("World")

world = decorator_example(world) #! Magic ?

world()
```

### Multiple decorators

- You can also apply more than one decorator to a function which accumulates their effects & makes decorators so helpful as reusable building blocks.

```python
def first_decorator(original_func):
    print("Big")
    return original_func

def second_decorator(original_func):
    print("Hello")
    return original_func

@second_decorator
@first_decorator
def world():
    print("World")

world()
```
- Output
```
Big
Hello
World
```
- The thing here to remember is that decorators applies in bottom to top order.
- If you break down the above example and avoid the `@` syntax to apply the decorators, the chain of decorator function calls looks like this:
```
world = second_decorator(first_decorator(world))
```


### Decorating functions that accept arguments

```python
def trace(original_func):

    def wrapper(*args, **kwargs):
        print(f'TRACE: calling {original_func.__name__}() '
              f'with {args}, {kwargs}')

        result = original_func(*args, **kwargs)

        print(f'TRACE: {original_func.__name__}() '
              f'returned {result!r}')
        return result

    return wrapper

@trace
def add(a, b):
    return a + b

print(add(5, 5))
```
- Output
```
TRACE: calling add() with (5, 5), {}
TRACE: add() returned 10
10
```
- There are two notable things going on with this decorator:
    - It uses the * and ** operators in the wrapper closure definition to collect all positional and keyword arguments and stores them in variables (args and kwargs).
    - The wrapper closure then forwards the collected arguments to the original input function using the * and ** “argument unpacking” operators.

### Where you can use decorators

- logging
- enforcing access control and authentication
- instrumentation and timing functions
- rate-limiting
- caching, and more

It’s cool to use decorators, but overuse of decorators makes your code tangled & unmaintainable in long run. You might end up annoying your colleagues. 

