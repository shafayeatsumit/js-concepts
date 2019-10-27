

#### spread & rest & destructuring



**Spread**

```js
const numbers = [1,2,3,4];
// pull out all the elements of array
// used for safe copy
const newNumbers = [...numbers, 5]; 
```

**rest**

```js
const filter = (...args) =>{
  return args.filter(el => el ===1)
}
console.log(filter(1,2,3,4))
==> [1]
```

**Destructuring**
extract array elements or object properties and assing then in variables.

```js
// array destructuring
[a,b] = ['Hello', 'Max']
// object destructuring
let {name} = {name:'Max' , age:28}
console.log(name) // Max
console.log(age) // undefined
```

