// let palindrome = 12321;

function palindromCheck(number) {
   let reversed = 0;
  let original = number;
    while(number > 0){
        let remainder = number % 10;
        reversed =  reversed * 10 + remainder;
        number = Math.floor(number/10);
    }
    return original === reversed;  //true or false
}

console.log(palindromCheck(121));

console.log("-------------------------------------------");

const arr =[1,2,3,4,5,6,9];
console.log("original array : ", arr);

const sliceArr =  arr.slice(1,3);
console.log("sliceArr : ", sliceArr);
console.log("AFTER slice a  array : ",arr );

console.log("-----------------SPLICE  array --------------------------");


const SpliceArr = arr.splice(1,3);
console.log("SpliceArr : ", SpliceArr);
console.log("After Splice a orginal  array : " , arr);

console.log("Check the type of array :  ", typeof arr);

console.log("-------------------------------------------");

const lang =["js","php","python","react","node"];
const dbs = ["mysql","mongodb","dynamoDB","postgress","mssql"];
  
//  note:- when we push a one array to another array it will not return a another array 

//   lang.push(dbs); //push array

// console.log(lang);

//note:- when we concate a two array it will return a new array 

const newConcatArr =  lang.concat(dbs);
// console.log("Merge the array with concat : ",newConcatArr);
const SpredArr = [...lang,...dbs];
console.log("Merge array with  Spred oprator : " , SpredArr);

console.log("-------------------------------------------");

const FArr =[1,2,4,5,[9,90],50,[6,7,[76,43,21],8]];

// note:- If we have a nested array and we want to make it a flat array so we can use flat() function to create a flat array.
// If we have n number of nested array into a array so that case we just pass the Infinity as a parameter for flat() function 

const flatArr = FArr.flat(Infinity);
// const flatArr = FArr.flat(2);  //we can pass the number also according to number of nested 
console.log("FLAT ARRAY : ", flatArr);

console.log("-------------------------------------------");

// note:- to check is array or not we can just use a Array.isArray() function and it return a true or false output

let chkArr=[2,3,4];

console.log("To check isArray : " , Array.isArray(chkArr));

console.log("----to create a array from a str----------");
// note:- when we want to create a array from a particular string we can use the Array.from() function like this:
const FormStr = "Sandeep";
console.log("str to array conversation : ", Array.from(FormStr));


console.log("----Array.of()----------");
// note:- Array.of() is use for  create a array of multiple variables like:
let a = 10;
let b = 20;
let c = 30;
console.log("Create a Array of variables : ", Array.of(a,b,c));


console.log("-------------Get Obj Keys --------------");
let obj = {
    name:"sandeep",
    city:"delhi",
    phone:9876543210,
    isActive:true,
    tech:["js","php","aws","nodejs"]
}
console.log(Object.keys(obj));

console.log("-------------Get Obj Values --------------");
console.log(Object.values(obj));

console.log("-----------Obj entries use ----------");
// note:- Object.entries use for create an Array of [key value] pairs form Object.
console.log(Object.entries(obj));

console.log("-------------hasOwnProperty--------------");
// note:- hasOwnProperty() :- is a method that returns a Boolean indicating whether an object has a property with the specified name.

console.log(obj.hasOwnProperty("isActive")); //checking a property into a object it's object property or not and return bool value.

console.log("-------------------------------------------");






function test(username) {
    return username;
}
console.log(test());
// note:- when we do not pass the argument into a function in that case function return undefined. (but if we already pass a default value for a parameter then it will never return a undefined value.)
console.log("--------------------------------------");

// Fabonachi series print ->
function FeboFunc(num){
    let num1 =0; let num2=1; let nextnum;
    let Arr =[];
    for(let i=1; i<=num; i++){
        Arr.push(num1);
        nextnum = num1+num2;
        num1 = num2;
        num2 = nextnum;
    }
    return Arr;
}
console.log(FeboFunc(10));
console.log("--------------------------------------");

// note:- when we are checking a scope in window console environment there different Global Scope and in a code environment Global scope is a different things.

// ----------------------------------------------

// const fun =  () => {
//     return  "test";
// }
// console.log(fun());

// ------------------------------------------------
// note:- When we print/console the `this` keyword  in a node environment(Global) it will console a empty object just because of in node global environment current time does not have a current data reference.
// note:- but when we console "this" keywork in a window environment then it will console the the windows object inside a console. 
 console.log(this); 
 
 
//  implicit and explicit in function-
const FunOne = (num1,num2) => (num1+num2);
console.log("implicit : ",FunOne(2,4));
// note:- This approach is called implicit return  (when we do not need to use return keyword and wrap output with () called implicit return function.)
// ---------------------------------------------------
const FunTwo = (num1,num2) =>{
    return num1+num2;
}
console.log("explicit : ",FunTwo(2,3));
// note:- This approach is called explicit return  (when we  need to use return keyword with curly brasses called explicit return function.)

console.log("-----Immediately Invoked Function Expressions IIFE----");

// syntax of IIFE :- ()();

// Note:- this is use for To avoid the global scope pollutions. (To remove the global scope variables declaration we use IIFE.)

(()=>{ console.log("IIFE function for immediate invocation.");})()


// FOREACH loop
const ArrLang =["JS","REACT.JS","NODE.JS","MONGODB"];
ArrLang.forEach((val)=>{ console.log(val)});




// -----function chaining--------
   function  Fun() {
    this.i = 1;
    this.add = function  (num) {
    this.i +=num;
    return this;
};
    this.print = function(){
    console.log(this.i);
    return this;
};
} 
let fun =   new Fun();
fun.add(2).print();

// ------------Prototype chaining--------

class Vehicle {
   constructor(make,model,year) {
       this.make = make;
       this.model = model;
       this.year = year;
   }
   
   start() {
       console.log(`starting: ${this.make}, ${this.model} , ${this.year}`);
   }

}
class Car extends Vehicle {
    drive() {
        console.log(`drive: ${this.make}, ${this.model} , ${this.year}`);
    }
}

let  car = new Car('Honda', 'Civic', 2023);

car.drive();
car.start();

// --------------prototype with function --------------
console.log("--------------prototype with function --------------");
function Person(name,age) {
    this.name =name;
    this.age = age;
    
}
Person.prototype.GreetingFun = function (){
    console.log(`Hello mr. ${this.name} your age is ${this.age}.`);
}

Person.prototype.checkAge = function () {
    if(this.age >20) { 
        console.log(`Hy! , Mr. ${this.name} You are eligible.`);
    } else {
    console.log(`Mr. ${this.name} You are not eligible.`);
    }
} 


 const person = new Person("test",22);
 person.GreetingFun();
 person.checkAge();
 
console.log("----------reduce method-------------------");
let rArr = [1,2,3,4]; let initialValue =1;
const ReduceVal = rArr.reduce((acc,cur)=>
{ return acc*cur },initialValue);
console.log("ReduceVal:", ReduceVal);

console.log("--------EVENT'S of JS-----");

addEventListner('click',()=>{ /* do some code or logic here*/},false); 
// note:- When we pass the false parameter into a addEventListner function it will work as Event bubbling by default it work event bubbling

addEventListner('click',()=>{ /* do some code or logic here*/},true);
// note:- But when we pass true parameter then it will work event capturing.


//  Prototype methods, objects without __proto__
//  let obj = {
//      tech:"js"
//  }

//  let new_tech = Object.create(obj);
//  console.log(new_tech.tech);
 
//  -------call  and this in js-----


// let nObj = {
//     name:"test name",
//     age:29,
//     grade:"A",
//     greeting:function(){
//         return  `Hello ${this.name} welcome.` 
//     }
// }

// let objChild = {
//     name:"child name",
//     age:30,
//     grade:"B"
// }
// const child = nObj.greeting.call(objChild);
// console.log(child);

// ---------------------------------------------------
// class  User {
//     constructor(username,email,password){
//         this.username = username;
//         this.email = email;
//         this.password = password;
//     }
    
//     UserPssEncpty (){
//         return `chk_${this.password}-#%!@`;
//     }
//     CreateUserID() {
//         return `${this.username}-21`;
//     }
// }

// let userOne = new User("test","test@gmail.com","testPass");
// console.log(`USER ONE Encription PAssword is :`,userOne.UserPssEncpty());
// console.log(`USER ONE Created User id is :`, userOne.CreateUserID());
// console.log("--------------------------------------");


// let UserTwo = new User("Dummy","dummy@gmail.com","dummyPss");
// console.log("USER TWO Encription Password is:",UserTwo.UserPssEncpty());
// console.log("USER TWO Created User id is: " , UserTwo.CreateUserID());


// --------------------------------------------------

// function User (username,email,password) {
//     this.username = username;
//     this.email = email;
//     this.password = password;
// }

// User.prototype.UserPssEncpty =function(){
//     return `@!#$${this.password}^%$`;
// }
// User.prototype.CreateUserID = function (){
//     return `${this.username}-321`;
// }


// let OneUser = new User("David","devid@gmail.com",321321);

// console.log("Encript password by function for user one:" ,OneUser.UserPssEncpty());


// console.log("created User id by function for one user is:" ,OneUser.CreateUserID());



// -------------Class ,super,construnctor,child,extends,inheritance,-------------------------

// class User  {
//     constructor(point){
//     this.point = point;        
//     }
//     DisplayPoint()  {
//          return `Your point is ${this.point}`   
//       }

//     }   

// class ChildUser extends User {
//     constructor(username,point,rating){
//       super(point);
//       this.username =username;
//       this.rating = rating;
//     }
    
//     displayName() {
//         return `Your name is ${this.username}.`;
//     }
// }


// let Un = new ChildUser("test",80,5);


// console.log(Un.DisplayPoint());
// console.log("AND");
// console.log(Un.displayName());

// // check the instanceOf----
// note- means it check instance/object  is drive from parent Class or not .It return true false value.
// example: if b is drive from A (b is a child of A ) it return true other wise it return false.
// console.log(Un instanceof User); //return true



// -------geter and seter in JS Object oriented---------
// note:- when we define a getter it must be define setter as well as if we are not creating a setter we can not use a getter.
// we have to use both:- get & set

// note:- in class who all properties we have so all properties method by default created (getter and setter).
// note:- getter: is use for getting a value .
// note:- setter: is use for setting  a value.

// note:- when we are setting a value using a setter method that time both constructor and setter both are setting a value so in this case there is a race between constructor and setter who will set a value first so in this scenario we got a error like :Maximum call stack size exceeded.
class User {
    constructor(username,password) {
     this.username = username;
     this.password = password;  
    }
    
  get password() {
      return `(*&)$-${this._password}-!#@$%^`;
  }
  set password(value) {
      this._password = value
  }
}

let OneUsr = new User("admin","321321");
console.log(OneUsr.password);



// 1:-
// note:- It will create a global exicution context here is two phase one is memory exicution  phase  and code exicution phase.First create a memory exicution phase where all variable and functions and class declare top into a memory exicutio phase so that time age var decrale with undefined value.

console.log("console var:", age);
var age = 20;
console.log("console var:", age);
// ---------------------------------------------------------
// 2:-
// note:- will throw the erro can not acces 'test' before initialization just becase of Temporal dead zone concept  apply for let const ina memory exicution .
// test = 100; 
// console.log(test);
// let test =30; 
// console.log(test);
// --------------------------------------------------------
// 3:-
// first time in memory exicution phase variable declare with myfun with unefined and then it hold the next funtion which value is "secound function" and code exicution time it reinitialize with first funtion whre value is"first function".

// myfun();
// var myfun = function() {
//     console.log("first function");
// }
// myfun();

// function myfun() {
//     console.log("secound function");
// }

// myfun();

// --------------------------------------------------------
// 4:-

// for(var i=1; i<=10; i++) {
//     setTimeout(()=>{ console.log(i) },1000);
// }


// -------------------------------------------------------
// 5:-
const Obj = {
    name:"test test",
    isActive:true,
    echek:function (){
        return `Hello ${this.name}, You are ${this.isActive}`;
    }
}
console.log(Obj.echek());
// -------------------------------------------------------
// 6:-
const Person = {
    height:30
};
console.log(Person.height); //30
 delete Person.height;
console.log(Person.height); //undefined
// -------------------------------------------------------





let arr =[1,2,3];
arr[arr.length]=4;
console.log(arr);
console.log("arr length is : ", arr.length);



//----------Insertion Array Element-------------
const ArrayInsertion = (ary,position,feling_ele) =>{
for(let i= ary.length-1; i>=0;i--) {
    if(i>=position) {
        ary[i+1] = ary[i];
        if(i==position) {
            ary[i] = feling_ele;
        }
    }
}
return ary;
}
let ary = [10,20,40,50,60];
let position = 2;
let  feling_ele = 70;
console.log("After Insertion Element :",ArrayInsertion(ary,position,feling_ele));


// ------------DELETE Element From An Array----------------
let DlArr =[2,4,9,7,5,4];
let positionD = 4;
for(let i=positionD; i<=DlArr.length-1; i++){
    DlArr[i] = DlArr[i+1];
}
DlArr.length = DlArr.length-1;
console.log(DlArr);
