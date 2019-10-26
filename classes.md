

#### classes

+ conveniet way of creating constructor function.
+ suuports inheritence 


**create a class**

```js
class Person {
  constructo(){
    this.name = "Max";
  }
  printMyName() {
    console.log(this.name)
  }
}
const person = new Person();
person.printMyName();
```

**inherti from a class**

```js
class Human {
  constructor(){
  	super(); // this is must, it executes parent constructor too.
    this.gender = 'male';
  }
  printGender() {
    console.log(this.gender);
  }
}

class Person extends Human {
  constructo(){
    this.name = "Max";
  }
  printMyName() {
    console.log(this.name)
  }
}
const person = new Person();
person.printMyName();
person.printGender();
```

**Why super**
+ if you extend another class and you implement constructor
+ Than super is a must.
+ super executes the parent constructor

**A es7 version of class**

```js
class Human {
  this.gender = 'male';
  printGender =() => {
    console.log(this.gender);
  }
}

class Person extends Human {
  name = "Max";
  printMyName = () => {
    console.log(this.name)
  }
}
const person = new Person();
person.printMyName();
person.printGender();
```