# Runner API Project

[[2023-06-06]]



Currently learning about Blueprints and Flask MethodViews

### What are Blueprints?
Each Flask Blueprint is an **object** that works very similarly to a Flask application. They both can have resources, such as static files, templates, and views that are associated with routes.

However, a Flask Blueprint is not actually an application. It needs to be registered in an application before you can run it. When you register a Flask Blueprint in an application, you’re actually **extending** the application with the contents of the Blueprint.

This is the key concept behind any Flask Blueprint. **They record operations to be executed later when you register them on an application.** For example, when you associate a view to a route in a Flask Blueprint, it records this association to be made later in the application when the Blueprint is registered.



### What are Method Views?
For APIs it can be helpful to use a different function for each HTTP method. [`MethodView`](https://flask.palletsprojects.com/en/2.2.x/api/#flask.views.MethodView "flask.views.MethodView") extends the basic [`View`](https://flask.palletsprojects.com/en/2.2.x/api/#flask.views.View "flask.views.View") to dispatch to different methods of the class based on the request method. Each HTTP method maps to a method of the class with the same (lowercase) name

[[2023-06-07]]
Swagger UI
### Marshmellow Schemas
The `marshmallow`[1](https://rest-apis-flask.teclado.com/docs/flask_smorest/marshmallow_schemas/#fn-1) library is used to define _what_ data fields we want, and then we can pass incoming data through the validator. We can also go the other way round, and give it a Python object which `marshmallow` then turns into a dictionary.

Schemas serve as the core of Marshmallow by keeping track of the data through the declared schema. The schemas define the structure of the data and also the validation of the data. We use schemas to validate incoming data to our API

```
class RunnersSchema(Schema):  
id = fields.Str(dump_only=True)  
first_name = fields.Str(required=True)  
last_name = fields.Str(required=True)  
half_marathon = fields.Str(required=True)  
marathon = fields.Str(required=True)
```


### Serialization vs Deserialization 
Data serialization is the process of converting structured data to a format that allows sharing or storage of the data in a form that allows recovery of its original structure. In some cases, the secondary intention of data serialization is to minimize the data’s size which then reduces disk space or bandwidth requirements.

#### Validating The Data
`Blueprint.arguments` - Validates and deserializaes a request payload
`Blueprint.response` - This doesnt perform validations. It just serializes the payload.

SQL Alchemy Intro
Connecting SQL Alchemy to pur app

[[2023-06-08]]
