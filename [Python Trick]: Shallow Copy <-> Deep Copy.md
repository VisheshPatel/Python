# Shallow Copy <-> Deep Copy

## Shallow Copy

```python
>>> xs = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
>>> ys = list(xs) # shallow copy
>>> xs
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
>>> ys
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```
- At this point, `ys` is new and independent object with the same contents as `xs`.
- Let's verify that
```python
>>> xs.append(['new sublist'])
>>> xs
[[1, 2, 3], [4, 5, 6], [7, 8, 9], ['new sublist']]
>>> ys
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```
- So far so good. Let's modify the sublist contents.
```python
>>> xs[1][0] = 'X'
>>> xs
[[1, 2, 3], ['X', 5, 6], [7, 8, 9], ['new sublist']]
>>> ys
[[1, 2, 3], ['X', 5, 6], [7, 8, 9]]
```
- You see, both `xs` & `xy` reflected the change. This happened because children/sublist were not copied. They were merely referenced again in the copied list. 

## Deep Copy
- Now that we have seen shallow copying. we can fix it by copying object actually/deeply. Thanks to copy module.
```python
>>> import copy
>>> xs = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
>>> zs = copy.deepcopy(xs)
>>> xsa
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
>>> zs
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```
- However, if you make a changes to sublist in the `xs`, you'll see that this won't affect the deep copied `zs`.
```python
>>> xs[1][0] = 'X'
>>> xs
[[1, 2, 3], ['X', 5, 6], [7, 8, 9]]
>>> zs
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```
- By the way, you can also create shallow copies using a function in the
copy module i.e. copy.copy().

## Shallow Copy of Primitive Types
```python
>>> class Point:
...     def __init__(self, x, y):
...         self.x = x
...         self.y = y
...
...     def __repr__(self):
...         return f'Point({self.x!r}, {self.y!r})'
... 
>>> a = Point(23, 42)
>>> b = copy.copy(a)
>>> a
Point(23, 42)
>>> b
Point(23, 42)
>>> a.x = 5
```
- Now, you might be expecting this change to reflect in `b` as well. But it won't:
```python
>>> a
Point(5, 42)
>>> b
Point(23, 42)
```
- Here, a thing to keep in mind is that there's no difference between a shallow & a deep copy when [primitive types](https://www.datacamp.com/community/tutorials/data-structures-python) are copied. 
