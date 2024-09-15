*Unpacking* in Python refers to:

1. An operation that consists of assigning an iterable of values to a [tuple](https://stackabuse.com/lists-vs-tuples-in-python/) (or `list`) of variables in a single assignment statement. 
2. As a complement, the term *packing* can be used when we collect several values in a single variable using the iterable unpacking operator, `*`.

For the purpose of this doc, we'll be focusing on 1.



Python allows a `tuple` (or `list`) of variables to appear on the left side of an assignment operation. Each variable in the `tuple` can receive one value (or more, if we use the `*` operator) from an iterable on the right side of the assignment.

```python
>>> # Unpacking strings
>>> a, b, c = '123'
>>> a
'1'
>>> b
'2'
>>> c
'3'
>>> # Unpacking lists
>>> a, b, c = [1, 2, 3]
>>> a
1
>>> b
2
>>> c
3
```

