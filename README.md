# TY_NGT

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





















































