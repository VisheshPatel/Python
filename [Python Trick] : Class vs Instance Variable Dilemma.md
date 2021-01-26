# Class vs Instance Variable Dilemma

- If you are coming from a statically typed language background, then you will surely be surprise by how Python's object model works!

# What Is Class Vs Instance Variable
- Class variables are used to share data b/w all instances of a class. They belong to a class, not a specific instance.
- Instance variables are unique to each instance. They belong to individual object instances and are not shared
among the other instances of a class.
```python
>>> class Dog:
...     num_legs = 4 # <- Class variable
...     
...     def __init__(self, name):
...         self.name = name # <- Instance variable
... 
>>> d1 = Dog('d1')
>>> d2 = Dog('d2')
>>> d1.name, d2.name
('d1', 'd2')
>>> d1.num_legs, d2.num_legs
(4, 4)
>>> Dog.num_legs
4
>>> Dog.name
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: type object 'Dog' has no attribute 'name'
```
- You see class variable(i.e. `num_legs`) can be accessed by instance/object or directly by the class itself.
- However, instance variable can't be accessed through the class.
  
# Distinction b/w Class Vs Instance Variable
```python
>>> Dog.num_legs = 6
>>> d1.num_legs, d2.num_legs
(6, 6)
>>> Dog.num_legs = 4
>>> d1.num_legs = 6
>>> d1.num_legs, d2.num_legs, Dog.num_legs
(6, 4, 4)
```
- As you can see, change in class variable reflects in all the instance/object. While change made in class variable through instance reflects only in that particular instance.
- That is because now the new `num_legs` instance variable "shadows" the class variable of the same name, overriding and hiding it when we access the object instance scope.
```python
d1.num_legs, d1.__class__.num_legs
(6, 4)
```

## How Does This Can Lead To A Problem
- Consider this implementation of faulty object counter:
```python
>>> class ObjectCounter:
...     num_instances = 0
...     
...     def __init__(self):
...         self.num_instances += 1 # !!!
... 
>>> ObjectCounter.num_instances
0
>>> ObjectCounter().num_instances
1
>>> ObjectCounter().num_instances
1
>>> ObjectCounter().num_instances
1
>>> ObjectCounter.num_instances   
0
```
- A solution
```python
>>> class ObjectCounter:
...     num_instances = 0
...     
...     def __init__(self):
...         self.__class__.num_instances += 1 # Have you noticed change?
... 
>>> ObjectCounter.num_instances
0
>>> ObjectCounter().num_instances
1
>>> ObjectCounter().num_instances
2
>>> ObjectCounter().num_instances
3
>>> ObjectCounter.num_instances   
3
```

