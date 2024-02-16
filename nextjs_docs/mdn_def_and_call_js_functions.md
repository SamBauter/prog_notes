# Review of JS for React
## Functions
```js
function square(number) {
    return number*number
}
```
### Function Expressions
```js
const square = function(number) {
return number * number
}
```

### Function expression with name (useful for recursion)
```js
const factorial = function fac(n){
    return n < 2 ? 1:n* fac(n-1)
}
console.log(factorial(3)) //6
```

### Functions that receive functions
Function expressions make it convenient to pass a function as an
argument to another function. Ex below fn is passed.
```js
function map(fn,a){
    const result = new Array(a.length)
    for (let i=0; i< a.length;i++){
        result[i] = f(a[i])
    }
    return result
}

const cube = function (x) {
    return x * x * x;
};

const numbers = [0, 1, 2, 5, 10];
console.log(map(cube, numbers)); // [0, 1, 8, 125, 1000]
```

### Functions Defined based on a condition
```js
let myFunc;
if (num === 0) {
    myFunc = function (theObject) {
        theObject.make = "Toyota";
    };
}
```
A `method` is a function that is a property of an object.

### Calling Functions
You can call them normally: `myFunc(5)`
They can call themselves recursively: 
```jsx
    function factorial(n) {
      if (n === 0 || n === 1) {
        return 1;
      } else {
        return n * factorial(n - 1);
      }
    }
```

### Function Hoisting
The below code works fine. This is because the JS interpreter
`hoists` the entire function declaration to the top of the current
scope. All function declarations are effectively at the top of the
scope. 
```jsx
console.log(square(5)); // 25

function square(n) {
return n * n;
}
```

ONLY WORKS WITH function declarations not function expressions

```jsx
console.log(square(5)); // ReferenceError: Cannot access 'square' before initialization
const square = function (n) {
  return n * n;
};
```





