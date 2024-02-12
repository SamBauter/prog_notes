# Rendering Lists
Display many similar components based on a collection.

Use `map()` and `filter()`

Notice that you can store arrays of jsx elements. The `listItems` here is just a bunch of jsx elements.
Ex:
```jsx
const listItems = people.map(person => <li>{person}</li>);
return <ul>{listItems}</ul>;
```

Note arrow function implicitly return the expression after => so you don't need to write `return`
UNLESS you follow `=>` with a `{` in which case you must explicitly write `return`

Arrow functions with `=> {` have a "block body" allowing you to write more than a single line of code.
But you must write `return` for them.

If you want to avoid react warnings each item needs a `key` attr that is unique. You need this for 
every call to `.map()` or other similar methods.
Ex: 
```jsx
<li key = {person.id}>...</li>
```
NOTE: Usually it's best to include keys in your data rather than trying to generate them on the fly.
Keys only need to be unique among siblings its okay to use same keys for jsx nodes in diff arrays.
Keys shouldn't change (don't generate them while rendering)
Where to get `key`?
1. DB primary keys for db data
2. Generate uuid for locally persisted data.

To display several DOM nodes for each item:
1. Easiest/Recommended way is to wrap them in a div which will let you pass a key.
2. Using `<></>` doesn't let you pass a key.
3. You can use the explicit `<Fragment> syntax` if you don't want divs in the
4. dom.

Note you don't need to have `key` defined as a param. It is going to get
stamped on the Recipe object for react to work with. You aren't using it
in the body of the Recipe function so don't need it. Note the key is needed
because you have an array of <Recipes> not divs.
Ex:
```jsx
function Recipe({ id, name, ingredients }) {
  return (
    <div>
      <h2>{name}</h2>
      <ul>
        {ingredients.map(ingredient =>
          <li key={ingredient}>
            {ingredient}
          </li>
        )}
      </ul>
    </div>
  );
}

export default function RecipeList() {
  return (
    <div>
      <h1>Recipes</h1>
      {recipes.map(recipe =>
        <Recipe {...recipe} key={recipe.id} />
      )}
    </div>)
```












