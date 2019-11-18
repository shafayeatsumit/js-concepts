### function constructor and prototype

#####  building object using function constructor
```
function constructors a normal function that is used to build OBJECTS. The this variable
points a new empty object and the object is returned from the function automatically
```

```
function Person() {
  this.firstName = 'John';
  this.lastName = 'Doe';
}
var john = new Person() // create object the JAVA way
console.log(john)
// {firstName: 'John', lastName:'Doe'}

functin Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

var john = Person('John', 'Doe') // creates a new object then returns
var sumit = Person('shafayeat','Kabir') // creates a new objectthen returns
console.log(Person.__proto__)
// Person {} 

```

#### life cycle of var john = new Person()

* when we write new an empty object is created
* then calls the function (eg: Person())
* execution context created 
* this will be pointing to that empty object created
* then return the object

 
##### how do we set prototype on function constructors 

* prototype property (.prototype) of a function is not the prototype (.__proto__) of the function
* .prototype is a special property of function
* properties are setup inside function constructors 
* methods are setting in the prototype (.prototype)
* we could setup in the constuctor as well but as functions are Objects it could take up the memory space
* another thing is if we create 1000 instances it will create 1000 object 
* it's better to keep them in prototype so every instance will refer one single method sits in the prototype (only one copy)


```
function Person (firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

Person.prototype.getFullName = function () {
  return this.firstName + ' ' + this.lastName;
}

// getFullName can be accessed by both of them
var john = new Person('John', 'Doe');
console.log(john)
console.log(john.getFullName())
// John Doe

var jane = new Person('Jane', 'Doe');
console.log(jane)
console.log(jane.getFullName())
// Jane Doe

Person.getFormalName = function () {
  return this.lastName + ', ' + this.lastName;
}
```

##### what if you forget the new keyword

```
var john = new Person('Shafayeat', 'Kabir') // valid this will return the Object
var john = Person('Shafayeat', 'Sumit') // will return undefined
```

##### Built in function constructors

```
var a = new Number(3);
var a = new String('sumit');
var a = new Date('01/11/2019');
// it is actually done by js automatilly so just "sumit" is same as the var a = new ('sumit')
```

##### why it is useful 
say we want to add a extra value to JS strings;

```
String.prototype.isLengthGreaterThan = function(limit) {
  return this.length > limit;
}

console.log("sumit".isLengthGreaterThan(3));

Number.prototype.isPositive = function(number){
  return number > 0;
}
3.isPositive() // throw error it will not convert
let a = new Number(3);
a.isPositive()
```

#### why it is dangerous

```
var a = 3;
var b = new Number (3);
//this coerces type 
a == b // true
// a is a primitive b is Object so it returns false, as we know === checks the type as well
a === b // false
```

#### array and for in 

```
var arr = ['shafa', 'kabir', 'sumit']
for (var i in arr) {
  console.log(i + ': ' + arr[i]);
}
// 0: shafa
// 1: kabir
// 2: sumit

// if somewhere else any framework adds feature to array
Array.prototype.customFeature = 'Cool'

// 0: shafa
// 1: kabir
// 2: sumit
// customFeature: cool
```
But why ???
Arrays are Objects in javascript. So those items are added properties. we can iterate down into the prototype.
 