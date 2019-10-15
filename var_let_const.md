## var, let, const



### variable declaration vs initialization

A variable declaration introduces a new identifier.

variable initialization is when you first assign a value to a variable

```
var declaration
console.log(declaration) // undefined
declaration = 'sumit' // now initialized
```

var VS let

var: 
  function scoped
  undefined when accessing a variable before it's declared

let: 
  block scoped
  ReferenceError when accessing a variable before it's declared
  

```
function discountPrices (prices, discount) {
  console.log(discounted) // ❌ ReferenceError

  let discounted = []

  for (let i = 0; i < prices.length; i++) {
    let discountedPrice = prices[i] * (1 - discount)
    let finalPrice = Math.round(discountedPrice * 100) / 100
    discounted.push(finalPrice)
  }

  console.log(i) // reference error
  console.log(discountedPrice) // reference error
  console.log(finalPrice) // reference error

  return discounted
}
```


```
consoel.log(x) //undefined
var x;
console.log(x)//ref error
let x;
```		

#### main takeaway

> var is function scoped \
> let is block scoped \
> const can not be reassigned 

#### resources
[tyler blog post](https://tylermcginnis.com/var-let-const/)
