Type Aliases - We can define a complicated type for a function return
or something else like
```js
function giveJson():{name:string,email:string}{
    return {name:"Sam",email:"samuelbauter@gmail.com"}
}
```
However sometimes objects are very complex with many properties,
for this we can use type aliases. These give us 3 nice things
1. a more meaningful name for the type
2. declare the shape of a type in a **single** place
3. import and export the type from modules
```ts
///////////////////////////////////////////////////////////
// @filename: types.ts
export type Amount = {
    currency: string
    value: number
}
///////////////////////////////////////////////////////////
// @filename: utilities.ts
import { Amount } from "./types"
function printAmount(amt: Amount) {
    console.log(amt)
    const {currency, value} = amt //Destructuring of amt into properties
    //Notice after destructing the properties have the types from Amount.
    console.log(`${currency} ${value}`)
}
// Still a structural type system
const donation = {
    currency:"USD",
    value:30.0,
    description:"donation to food bank"
}
printAmount(donation) //works fine and prints the currency + value
```

Declaring a type
```ts
type Amount = {
    currency:string
    value:number
}
type Amount = {
    fail: "this will not work" //causes Duplicate identifier error.
}
```
1. Rare occasion where type information is on rhs of assignment operator =.
2. Alias names have TitleCase.
3. Can only declare an alias of a given name once within a scope.

Using Type Aliases to simplify code:
```ts
///////////////////////////////////////////////////////////
// @filename: original.ts
import { flipCoin, success, fail } from './common'
/**
 * ORIGINAL version
 */
export function maybeGetUserInfo():
  | readonly ["error", Error]
  | readonly ["success", { name: string; email: string }] {
  // implementation is the same in both examples
  if (flipCoin() === 'heads') {
    return success
  } else {
    return fail
  }
}
 
///////////////////////////////////////////////////////////
// @filename: with-aliases.ts
import { flipCoin, success, fail } from './common'
 
type UserInfoOutcomeError = readonly ["error", Error]
type UserInfoOutcomeSuccess = readonly [
  "success",
  { readonly name: string; readonly email: string },
]
type UserInfoOutcome =
  | UserInfoOutcomeError
  | UserInfoOutcomeSuccess
 
/**
 * CLEANED UP version
 */
export function maybeGetUserInfo(): UserInfoOutcome {
  // implementation is the same in both examples
  if (flipCoin() === 'heads') {
    return success
  } else {
    return fail
  }
}
```

Inhertiance for type aliases is best accomplished by using intersection &
which naturally specifies further requirements on a type.
```ts
type SpecialDate = Date & { getDescription(): string } //Must have getDescription too

const newYearsEve: SpecialDate = Object.assign(
    new Date(),
    { getDescription: () => "Last day of the year" }
)
newYearsEve.getDescription() //autocompletion available
// there is not true extends keyword to be used when definiting type aliases
```
An interface is another way of defining an **object type**.
Object type refers to anonymous object contracts like on function returns, 
type aliases, and interfaces.

Interfaces can be imported exported between modules:
```ts
interface Amount {
    currency:string
    value:number
}
function printAmounts(amt:Amount){
    amt.currency //autocomplete
}
```
**Heritage clause** - SomeSubclass extends SomeMainClass
```ts
class AnimalThatEats {
  eat(food) {
    consumeFood(food)
  }
}
class Cat extends AnimalThatEats {
    meow() {
        return "meow"
    }
}
const c = new Cat()
c.eat
c.meow()
```
Same Heritage clause **extends** can be used with interfaces. This is the case
of a "sub-interface" extending a "base interface"
```ts
interface Animal{
    isAlive():boolean
}
interface Mammal extends Animal {
    getFurOrHairColor():string
}
interface Hamster extends Mammal {
    squeak():string
}
function careForHamster(h:Hamster){
    h.getFurOrHairColor()
    h.squeak()
    h.isAlive()
}
```
TS has a NEW heritage clause that can be used to state that a given class
should conform to a given interface: `implements`

```ts
interface AnimalLike{
    eat(food): void
}
class Dog implements AnimalLike{ //see the error for the class not having eat
    bark() {
        return "woof"
    }
}
```
TS has single inheritance and does not support true multiple inheritance
(extending more than one base class), however you can validate at compile time
that instances of a class conform more than one contract type. Implements allows
you to declare as many interfaces as you like, and you can use it in combination
with extends.
```ts
class LivingOrganism {
    isAlive(){
        return true
    }
}
interface AnimalLike {
    eat(food):void
}
interface CanBark {
    bark():string
}
class Dog2 extends LivingOrganism implements AnimalLike, CanBark {
    bark(){
        return "woof"
    }
    eat(food){
        consumeFood(food)
    }
}
```

You can use implements with type alias instead of interfaces. However, there
are some issues and you should prefer interfaces.
```ts
type CanJump = {
    jump():number } | string // this type is either something that has jump() or is a string
class Dog3 implements CanJump{ } //technically legal but avoid causes hard errors
```

Weird interface behavior: They can be declared twice in the same scope with different
contracts and the interface will be merged.
```ts
interface AnimalLike { // FIRST DEFINITION
  eat(food): void
}
function feed(animal: AnimalLike) {
    animal.eat
    animal.isAlive //Notice this is fine interface declarations 
    // are noticed 1st it seems
}
// SECOND DECLARATION OF THE SAME NAME
interface AnimalLike {
    isAlive(): boolean
}
```
This can be useful for augmenting existing or built-in types.

Choosing `type` vs `interface`
1. If you need to define something other than an object type (use of |) use a type alias.
2. If you need to defint a type to use with implements use an interface
3. If you want to allow consumers to augment your types use an interface.

Recursive types:
```ts
type NestedNumbers = number | NestedNumbers[]
const val: NestedNumbers = [3, 4, [5, 6, [7], 59], 221]
if (typeof val !== "number") { 
    val.push(41)// must perform check to see you don't have just 1 num 
// in that case you could not num.push()
val.push("my_string") // this will cause an assignment error 
// because it is not number | NestedNumbers[]
```



