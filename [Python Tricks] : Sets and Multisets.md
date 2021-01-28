# Sets and Multisets

- IMO, Sets and Multisets are the least used data structures in Python. Usually dev prefers list or dictionary. But when it comes to set & multiset, it has its own benefits in certain situations.
- So let me remind you quickly, how you can make use of it.

# Set
- A set is an unordered collection of objects that does not allow duplicate elements.
- You can declare set as:
```python
>>> vowels = {'a', 'e', 'i', 'o', 'u'}    # As you declare other collections
>>> squares = {x * x for x in range(10)}  # Or using comprehension
>>> 
>>> set_example = {}                      # This is not empty set
>>> type(set_example)                     # Its dictionary
<class 'dict'>
>>> set_example = set()                   # This is how you can declare empty set
```
- Set mostly employed when we need to test membership & compare b/w two collections.
![image](https://www.learnbyexample.org/wp-content/uploads/python/Python-Set-Operatioons.png)
- In set, membership tests are expected to run in fast O(1) time. While union, intersection, difference, and subset operations should take O(n) time on average. 
```python
>>> vowels = {'a', 'e', 'i', 'o', 'u'}
>>> 'e' in vowels
True

>>> letters = set('alice')
>>> letters.intersection(vowels)
{'a', 'e', 'i'}
```

# Frozen Set i.e. Immutable Sets
- You can modify the regular set we seen above. But sometimes you do not want to change the set once it is declared. In such cases, you can use:
```python
>>> vowels = frozenset({'a', 'e', 'i', 'o', 'u'})     
>>> vowels.add('p')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'frozenset' object has no attribute 'add'
```

# Multiset
- The `collections.Counter` class in the Python standard library implements a multiset type that allows elements in the set to
have more than one occurrence.
```python
>>> from collections import Counter
>>> inventory = Counter()

>>> loot = {'sword': 1, 'bread': 3}
>>> inventory.update(loot)
>>> inventory
Counter({'bread': 3, 'sword': 1})

>>> more_loot = {'sword': 1, 'apple': 1}
>>> inventory.update(more_loot)
>>> inventory
Counter({'bread': 3, 'sword': 2, 'apple': 1})
```
- Caveat for the `Counter` class is that it will return number of unique elements when `len()` is used.
