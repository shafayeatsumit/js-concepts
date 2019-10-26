

#### arrow function

an arrow function doesn't create it's own this context. 
+ this will always keep it's context in arrow function.
+ this keyword doesn't always refer to the context that you expect it to refer to. it points to the global Object. Arrow function solve this issue.

**this as global object**

```js
   function Person() {
    this.age = 0;
    setInterval(function(){
      this.age ++ // here this will refer global object      
    },1000)
   }
   var p = new Person()
```

**this as local object**
```js
   function Person() {
    this.age = 0;
    setInterval(()=>{
      this.age ++  // this will refer as person object.
    },1000)
   }
   var p = new Person()
```
#### resources
[FCC video](https://youtu.be/22fyYvxz-do?t=136)
