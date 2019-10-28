### By value By references


**copying an object creates an alias** both of the object points the same spot of memory. 


```js
//by value (primitives)
var a = 3;
var b;
b=a
a=2
console.log(a); // 2
console.log(b); // 3
```

```js
// by reference
var c = {greet: 'hi'}
var d ;
d=c
c.greet = 'hello';
console.log(c) // hello
console.log(d) // hello

function changeGreeting(obj){
  obj.greet = 'Hola';
}
changeGreeting(d)
console.log(c) // Hola
console.log(d) // Hola

// equals operator sets up a new memory space(new address)
c = {greet: 'Howdy'} // this is a brand new object
console.log(c) // Howdy
console.log(d) // Hola
```