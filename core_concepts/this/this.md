### THIS
Each exection context has
+ variable environment
+ outer reference
+ THIS variable
+ this will b pointing at different object depending on how the function is invoked

**for each execution context we have a specific THIS**

```js
console.log(this); // window OBJ

functions a() {
  console.log(this); // window OBJ
}

var b = function() {
  console.log(this); // window OBJ
}

a();
b();

var c = {
  name: 'The C Object',
  log: function() {
    console.log(this); // c OBJ
  }
}
c.log();
```
**what happens when we call THIS keyword in a function that sits inside a function inside an OBJECT**
```js
var c = {
  name: 'The C Object',
  log: function() {
  	this.name = 'Sumit'
    console.log(this); // c OBJ
    console.log(this.name); // Sumit
    
    var setName = function (newName){
      this.name = newName; // this will populate GLOBAL OBJECT . Ewwww!
    }
    setName('Kabir') 
    console.log(this); // Sumit // still the same . ????? 
    
  }
}
c.log();
```

**Doing The right way**
```js
var c = {
  name: 'The C Object',
  log: function() {
	// this is an OBJECT so it will set as a reference
    // this and self will point same location in the memory
  	var self = this; 
  	self.name = 'Sumit'
    console.log(this); // c OBJ
    console.log(this.name); // Sumit
    
    var setName = function (newName){
      self.name = newName; // c OBJ
    }
    setName('Kabir') 
    console.log(this); // Kabir 
    
  }
}
c.log();
```