``` python
class User
	def __init__(self,  user_id, username):
		#ATTRIBUTES
		self.id = user_id
		self.username = username
		self.followers = 0
		self.following = 0
		
		#METHODS
		def follow(self, user_to_follow):
			user_to_follow.followers +=1
		    self.following += 1	
		```

Classes are like blueprints. Objects are built from classes. 

# The Anatomy of A Class
- Attributes
	- Variables that are associated with an object. We could call these the nouns.
- Methods
	- Could call these the verbs.
- `__init__`
- Constructors
	- This says what happens when the class is called upon. 
	- `def __init__(self)`


