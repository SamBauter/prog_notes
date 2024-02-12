# Primer
## Values
Numbers:
```js
x = 5
y = 42.5
```
Strings:
```js
"Hello"
```
Booleans:
```js
true
false
```
Emptiness values:
```js
null
undefined 
```

Non primitive values / collections:
Arrays and Objects
```js
[1,2,3]
{name: "Kyle"}
```

Operators:
Comparisons are useful
```js
// 
3.0 == 3 //true checks for equality with type conversion
3.0 === 3 //true checks for equality without type conversion these are both numbers so
// there is no need for a type conversion.
//or 
true || false
```

## Types
Can always check with
```js
typeof 42 //number
typeof undefined // undefined
typeof null //object seen as a bug in JS we have to work around it
typeof [1,2,3] //object not super specific values can be subtypes of object type
```

## If and Else
```js
if (condition){
    //do something
}else{
    //do some other thing
}
```

## Loops
```js
for(let i = 0; i< student.length; i++){
}
//OR
for (let student of students) {
greetStudent(student)
}

//OR 

while (students.length > 0) {
    let student = students.pop()
    greetStudent(student)
}
```

## Functions
Group information and instructions into a procedure that can be re-used
```js
function greetStudent(student){
console.log(`Hello ${student.name}`)}
```









