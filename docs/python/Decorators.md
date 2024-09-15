Alright, imagine you have a magical pen that can change the appearance of your notebooks. Let's say you have a boring notebook, but with your magical pen, you can add cool designs or colors to it without changing the content inside. Decorator functions in Python are a bit like that magical pen.

In Python, functions are like the content of your notebook. They do stuff when you call them, like adding numbers or printing messages. Now, a decorator function is a special kind of function that can change or enhance other functions without actually changing their code.

Think of it this way: You have a plain function, let's call it "plain_notebook." It does its job, just like a plain, boring notebook. Now, you want to spice things up a bit. You create a decorator function, let's call it "decorate_notebook," which takes the plain notebook and adds some cool designs or colors to it.

```python
def decorate_notebook(plain_notebook_function):
    def decorated_notebook_function():
        print("Decorating the notebook...")
        plain_notebook_function()
        print("Notebook decorated!")
    return decorated_notebook_function

@decorate_notebook
def plain_notebook():
    print("This is a plain notebook.")

plain_notebook()

```


In this example, `decorate_notebook` is the decorator function. It takes `plain_notebook` as input, adds some extra stuff to it (printing messages before and after calling `plain_notebook`), and returns a new function called `decorated_notebook_function`. Then, we use the `@` symbol to apply the decorator to `plain_notebook`.

So when you call `plain_notebook()`, it actually calls `decorated_notebook_function()` instead. This means it will first print "Decorating the notebook...", then execute the code inside `plain_notebook` (which prints "This is a plain notebook."), and finally print "Notebook decorated!".

So, in short, decorator functions in Python allow you to modify or enhance the behavior of other functions without changing their code directly, similar to how a magical pen can change the appearance of a notebook without altering its contents.

Execution:

- Call `plain_notebook()`.
- `plain_notebook` is decorated, so it actually calls `decorated_notebook_function`.
- `decorated_notebook_function` adds extra functionality by printing messages and then calling the original `plain_notebook_function`.
- Finally, the execution completes after the messages are printed.