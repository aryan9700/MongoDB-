# MongoDB-
Cheatsheet
show dbs; // show all database present in mongo
use db Aryan; // use dbName to create a new database or switch to a database
db ; // view current database
db.dropDatabase('hawk'); //to delete database 

//for collection operation
show collection; // it show the collection we create inside database
db.createCollection('myComment'); // it create a new collection with given name =  'myComment' in database
db.myComment.drop(); // drop or delete a collection with name = myComment

//MongoDB commands for Rows
 //inserting of one row
db.comments.insert{(    
'name':'Aryan',
'class':12,
'sec':'D'
})
//insert of many Rows
db.comments.insertMany([{'name':'Aryan',
'class':12,
'sec':'d'},
{'name':'rohan',
'class':11,
'sec':'a'},
{'name':'krish',
'class':10,
'sec':'c'}])

//Command to view our created row
db.comments.find()
db.comments.find().pretty()
for copy pasting just click right button in mouse after copying
//command to view only limited Rows
db.comments.find().pretty().limit(2)
//command to find no. of Rows
db.comments.find().pretty().count()
db.comments.find({name:'rohan'}).count()
//Command to find the first row matching the object
db.comments.findOne({name:'Aryan'})


//Search in a MongoDB database
db.comments.find({name:'rohan',class:11})// if we write to find class of differents ids we get no reult

//Sorting of row in MongoDB
db.comments.find().sort({class:1}); //for ascending
db.comments.find().sort({class:-1}); //for decending

//Update a Row
db.comments.replaceOne({name:'aryan'},
{'name':'krishna'
,
'class':10,
'sec':'d'}),{upsert:true});
update not working

db.comments.replaceOne({name:'krish'},
{'name':'Aryan',
'class':11,
'sec':'a'})

//mongodb Increment Operator
db.comments.update({name:'rohan'},
{$inc:{
class:24
}})

//mongodb rename Operator
db.comments.update({name:'krish'},
{$rename:{
class:'batch'
}})
// to change every column name run this command without writing{name:'krish'} so it change all column name class to batch

//to remove
db.comments.remove({name:'Aryan'})

//all less than
db.comments.find({class:{$lt:20}})
//all greater than
db.comments.find({class:{$gt:20}})
//all greater then equal to
db.comments.find({class:{$gte:20}})
//all less than equal to
db.comments.find({class:{$lte:20}})
