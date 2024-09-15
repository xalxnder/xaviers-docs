
# Dump

Allows you to store JSON data directly into a file. It serializes the data, then writes to a file object

```python
import json  
  
test_dict = {  
    "name": "Xavier",  
    "age": 31  
}  
  
with open("test.json", "w") as file:  
    json.dump(test_dict, file, indent=4)

# test.json file

{  
    "name": "Xavier",  
    "age": 31  
}
```

# Load
Read and deserialize from a json file. 
```python

with open("test.json",  "r") as file:  
    data = json.load(file)  
    print(data)

# Output
{'name': 'Xavier', 'age': 31}

```

# Update