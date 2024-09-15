# Basics
HTTP request is client request to server. HTTP response is sever response back to client. For example, if you type url in web browser and hit `enter`, the browser creates an **http request** containing http method, request url, request headers and request body, which gets sent to the server. The server gets this and then sends info back  to the web browser.

### What Does This Have to Do With Flask?
This tripped me because I was routes, I was looking at from the perspective of a user. I thought I was creating the request. Nope! Here's some docs about flask responses:
```
The return value from a view function is automatically converted into a response object for you. If the return value is a string it’s converted into a response object with the string as response body, a `200 OK` status code and a _text/html_ mimetype. If the return value is a dict or list, `jsonify()` is called to produce a response. The logic that Flask applies to converting return values into response objects is as follows:
```