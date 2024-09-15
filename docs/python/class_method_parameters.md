If an attribute is used across multiple methods, it makes sense to define it as a class attribute. If a value is specific to a method, it makes sense to pass it as a parameter.

For example, if you have a method that needs to process a specific song or playlist, instead of setting the song or playlist as an attribute of the class, you could pass it as a parameter to the method.