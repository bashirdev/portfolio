const express =require("express");
const bodyParser =require("body-parser");
const request =require('request');
const _=require('lodash');

const ejs =require ("ejs");
const app = express();
app.set("view engine", 'ejs');
app.use(bodyParser.urlencoded({extends:true}));
app.use(express.static("public"));


let myArr=[];

let day=new Date();



let options={
    weekday: 'long',
    month: 'long',
    day:'numeric',
   
};
let today =day.toLocaleDateString("US-en" , options);



app.get('/', function(req, res){
    res.render('home');
});

app.get('/todolist', function(req,res){
    res.render('todolist', {newList:myArr, toDay:today});
});

app.post("/todolist" , function(req,res){
   const inputN=req.body.inputName;

   const myPost = myArr.push(inputN);

    res.redirect('/todolist');
});

app.get('/portfolio', function(req,res){
    res.render('portfolio');
});

app.get('/contact', function(req,res){
    res.render('contact');
});
app.get('/photography', function(req,res){
    res.render('photography');
});


app.listen(3000, function(){
    console.log("the server will be start on port 3000");
});

