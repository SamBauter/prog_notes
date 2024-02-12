# Passing Props to a component
React components use props to communicate with each other.
Parents can pass info to child components.
They look like html attributes but any JS function object or value can be passed.

Ex Normal passing of props to component:
```jsx
 <Avatar
      person={{ name: 'Lin Lanying', imageId: '1bX5QH6' }}
      size={100}
    />
```

Note double curlies are not special syntax 
1st: signal that this is JS
2nd: normal JS object syntax

Ex: Reading the props inside of a component:
```jsx
function Avatar({ person, size }) {
  return (
    <img
      className="avatar"
      src={getImageUrl(person)}
      alt={person.name}
      width={size})
```

Note you can use destructuring in the params to shorten your code.
However, **every component receives a single argument `props`**
Sometimes you don't need the whole props object in the component you are 
working in but you might need to pass it down.
Ex:
```jsx
function Avatar({ person, size, ...restProps }) {
// You can now use person, size in this component
    return ( 
        <div size = {size} id={person.id}>
// And restProps in a child component
    <AnotherComponent {...restProps} />
        </div>
    )
}
```

Components can also have default props in case they don't receive something.
```jsx
function Avatar({ person, size = 100 }) {}
```

Use spread sparingly. Sometime the more verbose passing of individual arguments
is more explicit and more legible.

Parent components that have a nested child will receive that content in a
`children` prop. These are usually visual wrappers panels grids divs etc.

```jsx
function Card({ children }) {
  return (
    <div className="card">
      {children}
    </div>
  );
}

export default function Profile() {
  return (
    <Card>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi',
          imageId: 'YfeOqp2'
        }}
      />
    </Card>
  );
}
```

Props are not always static but they are immutable. When a component needs
to change its props it will have to ask its parent to pass it a new props object.
This is done with state, don't try to change props.






