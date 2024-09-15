```python
>>> rows=range(1,4)
>>> cols=range(1,3)
>>> for row in rows:
	...     for col in cols:
	...             print(row,col)
...
1 1
1 2
2 1
2 2
3 1
3 2
```

This was a bit confusing at first. What helped me was to imagine the first loop as a counter, and the inner loop as something your doing {counter} amount of times. For each iteration of an outer loop the inner loop re-start and completes its execution before the outer loop can continue to its next iteration. Here's another example with strings.

```python
>>> adj = ["red", "big", "tasty"]
>>> fruits = ["apple", "banana", "cherry"]
>>> for x in adj:
	...     for y in fruits:
	...             print(x,y)
...
red apple
red banana
red cherry
big apple
big banana
big cherry
tasty apple
tasty banana
tasty cherry
```