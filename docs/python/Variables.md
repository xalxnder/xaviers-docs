### What is happening behind the scenes?
##### Object References


Python is a highly [object-oriented language](https://realpython.com/python3-object-oriented-programming/). In fact, virtually every item of data in a Python program is an object of a specific type or class. (This point will be reiterated many times over the course of these tutorials.)

```python
>>> print(300)
300
```


When presented with the statement `print(300)`, the interpreter does the following:
-   Creates an integer object
-   Gives it the value `300`
-   Displays it to the console


A Python variable is a symbolic name that is a reference or [pointer](https://realpython.com/pointers-in-python/) to an object. Once an object is assigned to a variable, you can refer to the object by that name. But the data itself is still contained within the object.

```python
n=300
```
This assignment creates an integer object with the value `300` and assigns the variable `n` to point to that object.

Now, what happens when we attempt to assign a variable to `n`?
```python
>>> n=300
>>> m=n
>>> m
300
```
What happens when it is executed? Python does not create another object. It simply creates a new symbolic name or reference, `m`, which points to the same object that `n` points to.
![[Pasted image 20221116054400.png]]

##### Reassignment
If you were to reassign n to foo, n will now point to foo. There is no longer any reference to the integer object `300`. It is orphaned, and there is no way to access it.

![[Pasted image 20221116054559.png | 800]]
### Object Identity 
In Python, every object that is created is given a number that uniquely identifies it. It is guaranteed that no two objects will have the same identifier during any period in which their lifetimes overlap. Once an object’s reference count drops to zero and it is garbage collected, as happened to the `300` object above, then its identifying number becomes available and may be used again.

After the assignment `m = n`, `m` and `n` both point to the same object, confirmed by the fact that `id(m)` and `id(n)` return the same number. Once `m` is reassigned to `400`, `m` and `n` point to different objects with different identities.

```python
>>> id(m)
4450787888
>>> id(n)
4450787888
>>>
```


#### Deep Dive
With the statement `m = 300`, Python creates an integer object with the value `300` and sets `m` as a reference to it. `n` is then similarly assigned to an integer object with value `300`—but not the same object. Thus, they have different identities, which you can verify from the values returned by `id()`.
```python 
>>> m = 300
>>> n = 300
>>> id(m)
60062304
>>> id(n)
60062896
```


But wait..
```python
>>> m = 30
>>> n = 30
>>> id(m)
1405569120
>>> id(n)
1405569120
```

Here, `m` and `n` are separately assigned to integer objects having value `30`. But in this case, `id(m)` and `id(n)` are identical!

For purposes of optimization, the interpreter creates objects for the integers in the range `[-5, 256]` at startup, and then reuses them during program execution. Thus, when you assign separate variables to an integer value in this range, they will actually reference the same object.