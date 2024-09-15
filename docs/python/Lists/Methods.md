### Adding/Removing

##### append
list.append(element)
This method adds an item to the end of a list. This does not return the new list, just modifies the original.
```python
>>> test = [1,2,3,4]
>>> test.append(5)
>>> test
[1, 2, 3, 4, 5]
```

##### index
list.insert(index, element) - inserts the element at the given index, shifting elements to the right
```python
>>> test.insert(1,1.5)
>>> test
[1, 1.5, 2, 3, 4, 5]
```

##### extend
list.extend(list2) - adds the elements in list2 to the end of the list. Using + or += on a list is similar to using extend().
```python
>>> lst2 = [6,7,8]
>>> test.extend(lst2)
>>> test
[1, 1.5, 2, 3, 4, 5, 6, 7, 8]
```

##### remove
list.remove(element) - searches for the FIRST instance of the given element and removes it (throws ValueError if not present)
```python
>>> test.remove(1.5)
>>> test
[1, 2, 3, 4, 5, 6, 7, 8]
```

##### sort
list.sort() - sorts the list in place (does not return it). (The sorted() function shown later is preferred.)
```python
>>> test = [4,3,55,1,53,4]
>>> test.sort()
>>> test
[1, 3, 4, 4, 53, 55]
```

##### reverse
list.reverse() - reverses the list in place (does not return it)
```python
>>> test.reverse()
>>> test
[55, 53, 4, 4, 3, 1]
```

##### pop
list.pop(index) - removes and returns the element at the given index. Returns the rightmost element if index is omitted (roughly the opposite of append()).
```python
>>> test
[55, 53, 4, 4, 3, 1]
>>> test.pop()
1
>>> test
[55, 53, 4, 4, 3]
```