TypesScript is an open source, typed syntactic superset of JS

Has 3 parts:
1. Language 
2. Language Server 
3. Compiler

```js
function add(a,b){
    return a+b //This works for string and numbers and more!
}
//Someone could interpret it as numbers and make bad changes
//TS makes it explicit
function add(a: number, b: number): number {
    return a + b
}
add(3, "4") //Throws Argument of type 'string' is not assignable to parameter of type number
```

Nominal Type systems
All about names you check the instance to see if it is of the right type name.
This is like in Java or Kotlin
Structural Type systems
Based on the structure of the objects not the constructor that was called
or the name of the class.
```ts
function printCar(car: {
  make: string
  model: string
  year: number
}) {
  console.log(`${car.make} ${car.model} (${car.year})`)
}
```
The function printCar doesn’t care about which constructor its argument came from, it only cares about whether it has:
- A make property that’s of type string
- A model property that’s of type string
- A year property that’s of type number
It would work for the following classes and instance:
```ts
class Car {
  make: string
  model: string
  year: number
  isElectric: boolean
}
 
class Truck {
  make: string
  model: string
  year: number
  towingCapacity: number
}
 
const vehicle = {
  make: "Honda",
  model: "Accord",
  year: 2017,
}
```

Union and Intersection Types
| symbol means OR These are Union Types
```ts
OneThroughFive | Evens => {1,2,3,4,5,6,8} //allowed 1-5 or evens
```

Intersection Types &
```ts
OneThroughFive & Evens => {2,4} //All of the values that are members of both!
```

The Union types are dramatically more common than the intersection types









