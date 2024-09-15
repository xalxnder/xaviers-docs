1. **json**: This parameter is used to send JSON data in the body of the HTTP request. When you pass a Python dictionary to the `json` parameter, `requests` automatically serializes the dictionary to JSON format and sets the appropriate Content-Type header to `application/json`. This is particularly useful when working with APIs that expect JSON data.
    
    
    

```python
    import requests  
    data = {"key": "value"} 
    response = requests.post(url, json=data)
    ```
    
    
2. **data**: This parameter is used to send form-encoded data in the body of the HTTP request. When you pass a dictionary to the `data` parameter, `requests` encodes the data as key-value pairs and sets the Content-Type header to `application/x-www-form-urlencoded`. This is commonly used when submitting HTML forms or interacting with APIs that expect form-encoded data.
    
    
```python
import requests

data = {"key": "value"}
response = requests.post(url, data=data)
```

In summary, use json when you want to send JSON data and data when you want to send form-encoded data or raw bytes.

#requests