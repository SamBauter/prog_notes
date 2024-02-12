# Objects
```js
const js = {
name:"Javascript",
isAwesome:true,
}
```

Objects have properties and values separated by colon.

 Object.freeze() makes existing properties non-writable and non-configurable. 
 New properties cannot be added.
 
# Object Methods
```js
const dog = {
    name: "Ein",
    breed: "Cordi",
    speak: function () {
        console.log("woof woof")
    }
}
```

You could also add a method as a new property.
```js
maggie.speak = function(){
console.log("woof")}
```

