# Types and coercion
Some people say:
"In JS everything is an object"
This is false there are primitive types
- undefined
- string
- number
- boolean
- symbol
- null?! - just weird sort of ignore
- function?! - subtype of object
- array?! subtype of object.

## The Nan Value
```js
var greeting = "Hello, class!";
var something = greeting /2; ////?!?!?!?!
Number.isNaN(something) //true
```

NaN doesn't really mean not a number ex:
```js
Number.isNaN(greeting) //false
```
Note how greeting is a string but results in false for the isNaN test.
Strings aren't number so shouldn't this be true?
NaN is a special value that indicates there was an invalid numeric operation
not just that something isn't a number.

## The new word
You should use new for constructors like:
- Object()
- Array()
- Function()
- Date()
- RegExp()
- Error()
Don't use new for these are produced via a function instead of a constructor:
- String()
- Number()
- Boolean

```js
var yesterday = new Date("March 6, 2019")
yesterday.toUTCString()

var myGPA = String(trascript.gpa) // Type conversion.
//"3.54
```

## Type Coercion
Some operators are overloaded to coerce
Ex:
```js
numStudents + ""
```
This is a common idomatic way to convert a type to a string because the + operator
is overloaded to attempt to coerce when one of the operands if it needs to.

## Falsy and Truthy
coercing to boolean produces false or true.
Falsy
0 -0 null NaN false undefined emptyString
Truthy
empty object
empty array

A quality JS program embraces coercion and tries to make types obvious

## Equality
"===": does not allow for coercion 
"==": allows for coercion
Both check values are equivalent ex: 3 == 3.0 //true

The == can sometimes be more convienient.
Ex: 
```js
var workshop1 = {topic: null}
var workshop2 = {}

if ( workshop1.topic === null || workshop1.topic === undefined)&&
(workshop2.topic === null || workshop2.topic === undefined)

vs. 
if( workshop1.topic == null && workshop2.topic == null) //this is more readable and
//because of coercion of undefined to null it works.
```




