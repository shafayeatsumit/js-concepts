# Call(), Apply(), Bind()

### Bind()

### Lets see an example
```
var person = {
    firstName : 'John',
    lastName: 'Doe',
    getFullName : function() {
        var fullName = this.firstName + " " + this.lastName;
        return fullName;
    }
}

var logName = function(lang1,lang2) {
    console.log("Logged: " + this.getFullName());
}


```

In the above example, in this line, `console.log("Logged: " + this.getFullName());`  **this** points to global
object. But I can control it so that it can point to `person` object. By using `logName.bind()` we can create
a copy of the logName function and inside the parenthesis, we can give whatever object I want to point `this` variable. Look at the snippet below:
> logName.bind(person);

we can use `bind` method like this:

```
var person = {
    firstName : 'John',
    lastName: 'Doe',
    getFullName : function() {
        var fullName = this.firstName + " " + this.lastName;
        return fullName;
    }
}

var logName = function(lang1,lang2) {
    console.log("Logged: " + this.getFullName());

}

var personLogName = logName.bind(person);

personLogName();

//output
Logged: John Doe
```
We can also use `bind` method like this
```
var person = {
    firstName : 'John',
    lastName: 'Doe',
    getFullName : function() {
        var fullName = this.firstName + " " + this.lastName;
        return fullName;
    }
}

var logName = function(lang1,lang2) {
    console.log("Logged: " + this.getFullName());

}.bind(person);

logName();

//output
Logged: John Doe
```

So that, `this.getFullName()` will now become `person.getFullName()`

### Call() and Apply()

+ when se say logName.call() it's the same as logName()
+ by using call() it lets me decide what would be the THIS variable
+ first arguments of CALL lets you decide which object is This for the function
+ **so bind creates a copy of the function , call just executes it**
+ appy does the same thing it just wants the parameters as a form of array
+ logName.call(person, "kabir", "sumit") logName.apply(person, ["kabir","sumit"])


```
var person = {
    firstName : 'John',
    lastName: 'Doe',
    getFullName : function() {
        var fullName = this.firstName + " " + this.lastName;
        return fullName;
    }
}

var logName = function(lang1,lang2) {
    console.log("Logged: " + this.getFullName());
    console.log('Arguments: ' + lang1 + ' ' + lang2);
    console.log('-----------');

}

//bind
var logPersonName = logName.bind(person);
logPersonName("bangla","english");

// call
logName.call(person,"bangla","english");

//apply
logName.apply(person,["bangla","english"]);

//output

Arguments: bangla english
-----------
Logged: John Doe
Arguments: bangla english
-----------
Logged: John Doe
Arguments: bangla english
-----------
```
In `Call()` and `Apply()` we can give whatever object we want to point `this` variable when we invoke that function!
Both are almost same but in `apply()` we need to give function parameter within array.



### Function  borrowing

```
var man = {
    firstName: 'Tony',
    lastname: 'Alica',
    getFullName : function() {
        var fullName = this.firstName + " " + this.lastname;
        return fullName;
    }
};

var man2 =  {
  firstName : 'Ashiqur',
  lastname : 'Rahman'
};


console.log(man.getFullName.apply(man2));

//output
Ashiqur Rahman
```
In the above example, both man and man2 object have same property `firstName` and `lastname`. I want to borrow
`man2's` value of `firstName` and `lastname` by invoking `man's` property. By using `apply` or `call` method we can get this feature.

# Function Currying
    CREATING A COPY OF A FUNCTION WITH SOME PRESET PARAMETERS
very useful in mathematical situations.

```
function multiply(a,b) {
    return a*b;
}

var multiplyBy2 = multiply.bind(this,2);
console.log(multiplyBy2(4));

var mutiplyBy3 = multiply.bind(this,3);
console.log(mutiplyBy3(5));

//output
8
15
```
In the above example, we set a permanent value of parameter `a` of `multiply` function by using `bind()`.
> var multiplyBy2 = multiply.bind(this,2); 

this code snippet set the value of a=2 which is permanent.
So when we invoke `multuplyBy2` function, we can only give the value of b.

Another way of doing this:
```
var f =  function(a,b) {
    return a*b;
}.bind(this,2);

console.log(f(8));
console.log(f(6));

console.log("------------------");

//output
16
12
````

