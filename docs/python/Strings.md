# Strings
Collections of text in Python are called **strings**. Functions used to manipulate strings are called string methods.

### Immutability
STRINGS ARE IMMUTBLE!! You can't change them once created.  You can't change the letters of a string.  If you want to change a string, do the following:

``````python
>>>word = "goal"
>>> word = "f" + word[1:]
>>> word
'foal'``
``````

Most string methods that alter a string, simply make a copy of it. If you want to actually keep the result, you need to assign it to a variable.

#tips

## String Literals 
Whenever you create a string by surroundng text with a quotation mark, the string is called a string literal. The quotes around the string literal are called **delimiters**

## Indexing and Slicing
 > The largest index in a string is always one less than the string's length.


You can extract a portion of a string, called a substring, by inserting a colon between two index numbers set inside square brackets. This is called **slicing**. 
For the next slicing examples, we'll be using the following:
```python
>>> flavor = "fig pie"
>>> flavor[0:3]
'fig'
```

Slicing can be super confusing. To remember how it works lets look at the following.

![[Pasted image 20220314194727.png]]

 > If you omit the first index in a slice, Python assumes you want to start at index 0.
 ```python
>>> flavor = "fig pie"
>>> flavor[:3]
'fig'
```


>  If you omit the 2nd index, you start at that index, and go until the end of the string.

```python
>>> flavor[3:]
 ' pie'
```

The rules for slicing with negative numbers are exactly the same as th erules for slicing with positive numbers
![[Pasted image 20220316192504.png]]
> To go backwards, omit the starting postion, and ending position. Then for the step, use -1.
```python
>>> lst = [2,4,6,8]
>>> lst[::-1]
[8, 6, 4, 2]
```

### String Methods 
- .rstrip()
- .lstrip()
- .strip
- .upper()
- .lower()
- .endswith()
- .startswith()


