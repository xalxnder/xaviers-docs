# Syntax Errors
A syntax error occurs when you write code that isnt allowed in the Python language.  The following would produce a syntax error. These are caught before a program even starts running. 
```python
print("Hello World)

EOL while scanning stirng literal

```
1. A string literal is the text enclosed in quotes.
2. EOL stands for end of line. 


# Runtime Errors
These only occur when a program is running.

Whenever an error occurs, python stops executing the program and displays several lines of text called a traceback.
```python
Traceback (most recent call last):
  File "/home/hello_world.py", line 1, in <module> 

 print(Hello, World)
NameError: name 'Hello' is not defined
```

 These are best read from the bottom up.
 1. The last line tells you the name of the error.
 2. The second to last line shows you the code that produced the error.
 3. The third to last line tells you the name of the file and the line number so you can go to the exact spot  of the error. 


