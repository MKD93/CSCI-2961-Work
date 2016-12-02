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
from pymongo import MongoClient
from pprint import pprint
import random
import time
import datetime

client = MongoClient()
db = client['csci2963']
collection = db['definitions']

if __name__ == '__main__':
    index = random.randint(0, collection.count() - 1)
    record = collection.find().limit(-1).skip(index).next()
    time = datetime.datetime.now().strftime("%y-%m-%d-%H-%M")
    
    pprint record
    collection.update({"word" : record["word"]}, {"$push" : {"dates" : time}})
    pprint record
```
