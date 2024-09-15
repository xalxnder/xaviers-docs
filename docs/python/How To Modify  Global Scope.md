
```python
enemies = 1

#This wont work
def increase_enemies():
    enemies += 1
    print(enemies)


#Option 1...but bad practice 
def increase_enemies():
	global enemies 
    enemies += 1
    print(enemies)

#Option 2 - > Using return 
enemies = 1
def increase_enemies():
    return enemies + 1
```



When To Use Global Variables

1. When using constants.
	1. Something you define, but will NEVER change.


#tips 