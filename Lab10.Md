##Checkpoint 4
```
from pymongo import MongoClient
from pprint import pprint
from bson.objectid import ObjectId

client = MongoClient()
db = client['csci2963']
collection = db['definitions']
posts = db['posts']

cursor_F = collection.find()
cursor_F1 = collection.find_one()
cursor_FS = collection.find({u'word' : u'Capitaland'})
cursor_FR = collection.find({u'_id' : ObjectId(u'56fe9e22bad6b23cde07b8cb')})

post = {u'word' : u'Test123', u'definition' : u'test definition'}
posts.insert_one(post)

if __name__ == '__main__':
    for document in cursor_FR: 
        pprint(document)
```
##Checkpoint 5
```
```
