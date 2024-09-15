
Use tuples when you want to create a list of items that does not change. 
```python
>>> dimensions = (0,200)
>>> dimensions[0] = 10
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

##### But wait!
Although you can’t modify a tuple, you can assign a new value to a variable that represents a tuple.
```python
>>> print(dimensions)
(0, 200)
>>> dimensions = 200,400
>>> print(dimensions)
(200, 400)
>>>
```

Sidenote - You don't need parentheses. Tuples are technically defined by the presence of a comma; the parentheses make them look neater and more readable. If you want to define a tuple with one element, you need to include a trailing comma: