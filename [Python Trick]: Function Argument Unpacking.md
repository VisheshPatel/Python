Python has really cool feature of function argument unpacking which works as follow:
- To print coordinate you have written something like:
```python
>>> def print_coordinate(x, y, z):
...     print('<{}, {}, {}>'.format(x, y, z))
... 
>>> print_coordinate(1, 2, 3)      
<1, 2, 3>
```
- But, if the data structure for storing coordinate taken tuple, then it will bit awkward/over-verbose to print coordinates:

```python
>>> tuple_coordinate = (4, 5, 6)
>>> print_coordinate(tuple_coordinate[0],
...                 tuple_coordinate[1],
...                 tuple_coordinate[2])
<4, 5, 6>
```

- However, with function argument unpacking, you can explode the any iterable before passing it to function.

```python
>>> tuple_coordinate = (4, 5, 6)
>>> print_coordinate(*tuple_coordinate)
<4, 5, 6>
>>> list_coordinate = [7, 8, 9]
>>> print_coordinate(*list_coordinate)
<7, 8, 9>
```

- This works with generator expression too.

```python
>>> gen = (x * x for x in range(3))
>>> print_coordinate(*gen)
<0, 1, 4>
```

- Though for dictionary we have slightly different approach

```python
>>> dict_coordinate = {'z': 0, 'y': 1, 'x': 2}
>>> print_coordinate(*dict_coordinate)      # Explode keys
<z, y, x>
>>> print_coordinate(**dict_coordinate)     # Explode values
<2, 1, 0>
```

- The thing to note in case of dictionary value unpacking is that dictionary values are selected based on function arguments taken as keys: the `x` argument receives the value associated with the `x` key in the dictionary & so on.
