# TY_NGT

## 1. MongoDB Basics <Br>
1.a Write a MongoDB query to create and drop database. <br>
create db
```js
use college
```
drop database
```js
db
db.dropDatabase()
```

1.b create collection, show, drop collection
```js
db.createCollection('student')
show collections
db.student.drop()
```

1.c Write a MongoDB query to insert, query, update and delete a document.
insertOne()
```js
db.students.insertOne({
  "name": "John Doe",
  "rollno": "C101"
})
```
insertMany()
```js
db.students.insertMany([
  {
    "name": "Jane Smith",
    "rollno": "C102"
  },
  {
    "name": "Bob Johnson",
    "rollno": "C103"
  }
])
```
 updateOne
 ```js
db.students.updateOne(
  { "rollno": "C101" },
  { $set: { "contact": "123-456-7890" } }
)
```
updateMany
```js
db.students.updateMany(
  { "class": "10th" },
  { $set: { "contact": "N/A" } }
)
```
deleteOne
```js
db.students.deleteOne({ "rollno": "C101" })
```
deleteMany
```js
db.students.deleteMany({ "class": "10th" })
```

## 2. Simple Queries with MongoDB
step 1: open cmd from below path
```
c:\Program Files\MongoDB\Tools\100\bin
```
step 2: import csv
```js
mongoimport --db college --collection student1 --type csv --file [csv file location] --headerline
```
step 3: find()
```js
db.student1.find({}, {FName:1, Age:1, Score:1})
```
```js
db.student1.find({Gender:"Female"}, {FName:1, Age:1}).pretty()
```
```js
db.student1.find({Age:{$gt:25}}).pretty()
```
Display first 6 records of male students
```js
db.student1.find({Gender:"Male"}).limit(6)
```
Display record of female students whose score is more than 60
```js
db.student1.find({$and:[{Gender:"Female"}, {Score:{$gt}}]})
```
## 3. Implementing Aggregation
3.a Write a MongoDB query to use sum, avg, min and max expression.<br>
sum 
```js
db.student1.aggregate([{$group:{_id:"$GENDER", totalscore:{$sum:"$SCORE"}}}])
```
min
```js
db.student1.aggregate([{$group:{_id:"$GENDER", minscore:{$min:"$SCORE"}}}])
```
max
```js
db.student1.aggregate([{$group:{_id:"$GENDER", maxscore:{$max:"$SCORE"}}}])
```
avg or average
```js
db.student1.aggregate([{$group:{_id:"$GENDER", avgscore:{$avg:"$SCORE"}}}])
```
match
```js
db.student1.aggregate([{$match:{GENDER:"Female"}},{$group:{_id:"$GENDER",minage:{$min:
"$AGE"}}}])
```
3.b Write a MongoDB query to use push and addToSet expression.<br>
3.b.1 insert whole thing as array
```js
db.student1.update({"FNAME":"Dave"},{$push:{"language":["mongoDB","Java"]}})
```
3.b.2 treat each element individually.
```js
db.student1.update({"FNAME":"Rose"},{$push:{"language":{$each:["C","C++","python"]}}})
```

3.b.3 same as push.. check before inserting.. didn’t insert if already exists.
```js
db.student1.update({"FNAME":"Rose"},{$addToSet:{"language":{$each:[".NET"]}}})
```

3.c Write a MongoDB query to use first and last expression.
 ```js

```


## 4. Replication, Backup and Restore
4.b Backup
```js
mongodump --host <your_host> --port <your_port> --username <your_username> --password <your_password> --out <backup_directory>
```
example
```js
mongodump --host localhost --port 27017 --username myuser --password mypassword --out /path/to/backup_directory
```

4.c restore
```js
mongorestore --host <your_host> --port <your_port> --username <your_username> --password <your_password> --drop --dir <backup_directory>
```
example
```js
mongorestore --host localhost --port 27017 --username myuser --password mypassword --drop --dir /path/to/backup_directory
```

## 7. Python and MongoDB
Connecting Python with MongoDB and inserting, retrieving, updating and
deleting.
```cmd
pip install pymongo
```
insert.py
```py
import pymongo
myclient = pymongo.MongoClient("mongodb://localhost:27017")
mydb=myclient["mydatabase"]
mycol=mydb["customer1"]
mydict={"name":"ramesh", "address":"goregoan", "age":20}
x=mycol.insert_one(mydict)
print(x.inserted_id)
for x in mycol.find():
    print(x)
```
retrieve.py
```py
import pymongo
myclient = pymongo.MongoClient("mongodb://localhost:27017")
mydb=myclient["mydatabase"]
mycol=mydb["customer1"]
for x in mycol.find():
    print(x)
```
update.py
```py
import pymongo
myclient = pymongo.MongoClient("mongodb://localhost:27017")
mydb=myclient["mydatabase"]
mycol=mydb["customer1"]
myquery={"address":"goregoan"}
newval={"$set":{"address":"mumbai"}}
mycol.update_one(myquery,newval)
for x in mycol.find():
    print(x)
```
delete.py
```py
import pymongo
myclient = pymongo.MongoClient("mongodb://localhost:27017")
mydb=myclient["mydatabase"]
mycol=mydb["customer1"]
myquery = {"address":"mumbai"}
mycol.delete_many(myquery)
print("document deleted")
```

## 8. jQuery Basics
## 8a. jQuery Basic, jQuery Events <br>
8.a.1 click event
```html
<!Doctype html>
<html>
<head>
<script src="https://code.jquery.com/jquery-3.7.1.min.js">
</script>
<script>
$(document).ready(function(){
$("p").click(function(){
$(this).hide();
});
});
</script>
</head>
<body>
<p>This text will be disapper if you click
on it. </p>
<p>Click to make this text disapper</p>
<p>Click here to make it disapper</p>
</body>
</html>
```
8.a.2 double click event
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("p").dblclick(function () {
                $(this).hide();
            });
        });
    </script>
</head>

<body>
    <p>This text will be disapper if you
        double click on it. </p>
    <p>Double Click to make this text
        disapper</p>
    <p>Double Click here to make it
        disapper</p>
</body>
</html>
```

## 8b. jQuery Selectors, jQuery Hide and Show effects
8.b.1 jQuery selector
```html
<!Doctype html>
<html>
<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            //element selector
            $("p").css("background-color", "yellow");
            $("button").click(function () {
                //ID selector
                $("#myid").hide();
            });
        });
    </script>
</head>

<body>
    <p>Paragraph 1 </p>
    <p id="myid">Paragraph 2</p>
    <p> Third Paragraph</p>
    <button>click me to hide text</button>
</body>
</html>
```

8.b.2 jQuery Hide and Show effects
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("#b1").click(function () {
                $("p").hide();
            });
            $("#b2").click(function () {
                $("p").show();
            });
        });
    </script>
</head>

<body>
    <h2> Welcome to TYBSc IT </h2>
    <p>Paragraph 1 </p>
    <p>Paragraph 2</p>
    <button id="b1">Click here to hide paragraph</button>
    <button id="b2">Click here to show paragraph</button>
</body>

</html>
```
## 8.c jQuery fading effects, jQuery Sliding effects <br>
8.c.1 jQuery fading effects
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("#b1").click(function () {
                $("p").fadeIn();
            });
            $("#b2").click(function () {
                $("p").fadeOut();
            });
            $("#b3").click(function () {
                $("p").fadeToggle();
            });
        });
    </script>
</head>

<body>
    <h2> Welcome to TYBSc IT </h2>
    <p>Paragraph 1 </p>
    <p>Paragraph 2</p>
    <button id="b1">Click here to Fade In</button>
    <button id="b2">Click here Fade out</button>
    <button id="b3">Click here Fade toggle</button>
</body>
</html>
```

8.c.2 jQuery Sliding effects
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("#b1").click(function () {
                $("p").slideUp();
            });
            $("#b2").click(function () {
                $("p").slideDown();
                $("p").css("color", "red");
            });
            $("#b3").click(function () {
                $("p").slideToggle();
            });
        });
    </script>
</head>

<body>
    <h2> Welcome to TYBSc IT </h2>
    <p>Paragraph 1 </p>
    <p>Paragraph 2</p>
    <button id="b1">Click here to SlideIn</button>
    <button id="b2">Click here SlideOut</button>
    <button id="b3">Click here SlideToggle</button>
</body>
</html>
```

## 9.a jQuery Animation effects, jQuery Chaining
9.a.1 jQuery Animation effects
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("button").click(function () {
                $('#myDiv').animate({
                    height: '200px',
                    width: '200px',
                    left: '500px',
                });
            });
        });
    </script>

    <style>
        .redDiv {
            background-color: red;
            height: 100px;
            width: 100px;
            position: absolute;
        }
    </style>
</head>

<body>
    <h1>Demo: jQuery animate() method</h1>
    <button>click</button>
    <div id="myDiv" class="redDiv">
    </div>
</body>

</html>
```

9.a.2 jQuery Chaining
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("button").click(function () {

                $("#p1").css({ "color": "red", "font-size": 50 })
                    .slideUp(2000)
                    .slideDown(2000);
            });
        });
    </script>

</head>

<body>
    <p id="p1">jQuery is fun!!</p>
    <button>Click me</button>
</body>

</html>
```
## 9.b jQuery Callback, jQuery Get and Set Contents <br>
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("button").click(function () {
                $("p").hide("slow", function () {
                    alert("The paragraph is now hidden");
                });
            });
        });
    </script>

</head>

<body>
    <button>Hide</button>
    <p>This is a paragraph with little content.</p>
</body>

</html>
```
## 9.c jQuery Insert Content, jQuery Remove Elements and Attribute
9.c.1 jQuery Insert Content
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("#btn1").click(function () {
                $("p").prepend(" <b>Appended text</b>.");
            });
            $("#btn2").click(function () {
                $("ol").append("<li>Appended item</li>");
            });
        });
    </script>

</head>

<body>
    <p>This is a paragraph.</p>
    <p>This is another paragraph.</p>
    <ol>
        <li>List item 1</li>
        <li>List item 2</li>
        <li>List item 3</li>
    </ol>
    <button id="btn1">Prepend
        text</button>
    <button id="btn2">Append list
        items</button>
</body>

</html>
```
9.c.2 jQuery Remove Elements
```html
<!Doctype html>
<html>

<head>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js">
    </script>
    <script>
        $(document).ready(function () {
            $("button").click(function () {
                $("p").remove(".test");
            });
        });
    </script>

</head>

<body>
    <p>This is a paragraph.</p>
    <p class="test">This is another
        paragraph.</p>
    <p class="test">This is another
        paragraph.</p>
    <button>Remove all p elements with
        class="test"</button>
</body>

</html>
```

## 10. JSON
10.a Creating JSON
```py
import json
x = {"name":"John", "age":20, "city": "mumbai"}
y = json.dumps(x)
print(y)
```

10.b Parsing JSON
```py
import json
x = '{"name":"John", "age":20, "city": "mumbai"}'
y = json.loads(x)
print(y["age"])
```
10.c Parsing JSON
```py
import json

# Sample JSON data
data = {"name": "John", "age": 30, "city": "New York"}

# Writing JSON data to a file
with open("example.json", "w") as json_file:
    json.dump(data, json_file, indent=4)

# Reading JSON data from the file
with open("example.json", "r") as json_file:
    loaded_data = json.load(json_file)

# Modifying the data
loaded_data["age"] = 31
loaded_data["city"] = "San Francisco"

# Writing the modified data back to the file
with open("example.json", "w") as json_file:
    json.dump(loaded_data, json_file, indent=4)
```

## 11. Create a JSON file and import it to MongoDB
11.a Export MongoDB to JSON.
```js
mongoexport --host <your_host> --port <your_port> --username <your_username> --password <your_password> --db <your_database> --collection <your_collection> --out <output_file.json>
```
example
```js
mongoexport --host localhost --port 27017 --username myuser --password mypassword --db mydatabase --collection mycollection --out /path/to/output_file.json
```

