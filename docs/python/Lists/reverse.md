How To Reverse a List?

# Using reverse() method  
```python
my_list = [1, 2, 3, 4, 5]  
my_list.reverse()  
print(my_list)  # Output: [5, 4, 3, 2, 1]  
  ```
# Using slicing  
```python
my_list = [1, 2, 3, 4, 5]  
reversed_list = my_list[::-1]  
print(reversed_list)  # Output: [5, 4, 3, 2, 1]
```



- my_list = [1, 2, 3, 4, 5]: This line is creating a list of integers from 1 to 5 and assigning it to the variable my_list.  
- reversed_list = my_list[::-1]: This line is using slicing to create a reversed copy of my_list. The [::-1] part is the slicing syntax. The colon : is used to indicate the start and end indices. When no index is provided before the first colon, it means start from the beginning. When no index is provided after the first colon, it means go till the end. The -1 after the second colon indicates the step, which in this case is -1, meaning go backwards.  
- print(reversed_list): This line is printing the reversed list to the console. The output is [5, 4, 3, 2, 1], which is the list [1, 2, 3, 4, 5] in reverse order.