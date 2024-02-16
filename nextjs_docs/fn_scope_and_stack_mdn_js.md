# Function scope.
Variables defined in a function cannot be accessed outside of it.
A function however can access all vars from all of the outer scopes,
even if it is nested quite deep.

```js
const num1 = 20;
const num2 = 3;
const name = "Chamakh";

// A nested function example
function getScore() {
    const num1 = 2; //override outer scope
    const num2 = 3; // override outer scope

    function add() {
        //name accessed 2 scopes deep
        return `${name} scored ${num1 + num2}`;
    }

    return add();
}
console.log(getScore()); // "Chamakh scored 5"
```

## Recursion
3 ways a function can refer to itself:
1. The function's name
2. `arguments.callee`
3. An in-scope variables that refers to the function.

```js
const foo = function bar() {
  // statements go here
};
```
Within the function body the following are all equivalent:
1. `bar()`
2. `arguments.callee()`
3. `foo()`

Recursive functions have base conditions to `return` from
```js
function walkTree(node) {
  if (node === null) {
    return;
  }
  // do something with node
  for (let i = 0; i < node.childNodes.length; i++) {
    walkTree(node.childNodes[i]);
  }
}
```
Subsequent calls in the function are added to the
`function stack` and popped off as they return

## Nested functions and closures
You can nest functions inside other functions. The nested function
is private to its containing function and cannot be accessed in
global scope.

It also forms a `closure` - an expression (most commonly, a function)
that can have free variables together with an environment that binds
those variables (that "closes" the expression).

Nested functions can "inherit" the arguments and variables of the 
containing function. The inner function contains the scope of the outer
function.

**The inner function forms a closure: it can access the arguments and
variables of the outer function, BUT the outer function cannot use the args
and variables of the inner function.**

Sometime closures can be used to modify function behaviors by returning
functions. Sometimes you will see the double call syntax because the
first call returns a function and the second calls the returned function.

Ex:
```js
function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}

const fnInside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give it
console.log(fnInside(5)); // 8
console.log(outside(3)(5)); // 8
```

x is preserved in `fnInside`. Because `inside` has closure over x.
A closure must preserve the arguments and variables in all scopes it references.








