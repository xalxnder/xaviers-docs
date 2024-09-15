# Walrus Operator

Introduced in Python 3.8, the walrus operator allows us to assign variables from within an expression 
```python
>>> num = 15
>>> print(num)
15


#Again, but using the walrus opertor.
>>> print(num:=15)
15
```

Another example:

```python
 >>> tweet_limit = 280  
>>> tweet_string = "Blah" * 50  
>>> diff = tweet_limit - len(tweet_string) >>> if diff >= 0:  
... print("A fitting tweet")  
... else:  
... print("Went over by", abs(diff)) ...  
A fitting tweet

#Again, but using the walrus operator.

>>> tweet_limit = 280  
>>> tweet_string = "Blah" * 50  
>>> if diff := tweet_limit - len(tweet_string) >= 0: ... print("A fitting tweet")  
... else:  
... print("Went over by", abs(diff))  
...  
A fitting tweet
```