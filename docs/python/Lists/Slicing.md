You can work with a specific group of items in a list , called a slice. To make a slice, you specify the index of the first and last elements you want to work with. As with the range() function, Python stops one item before the second index you specify.

To better understand slicing, lets use some visuals
```python
>>> colors = ["red", "blue", "yellow", "green", "black"]
>>> print(colors[0:2])
['red', 'blue']

0       1         2            3           4           5
| red | blue | yellow | green | black |
-5      -4       -3          -2          -1         0
```

If you omit the 1st index, ,python starts at the beginning of the list. If you omit the 2nd index, ,python goes until the end of the list. 

We can also use slicing to copy an entire list. 
```python
>>> more_colors = colors[:]
>>> print(more_colors)
['red', 'blue', 'yello', 'green', 'black']
```