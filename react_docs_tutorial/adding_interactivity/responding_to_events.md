# Event Handlers

To add an event handler you will define the function and pass it as a prop.

```jsx
export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

Usually defined inside your component functions with name that starts with
handle. Can also define it inline.
```jsx
<button onClick={function handleClick() {
  alert('You clicked me!');
}}>
```

Or inline with arrow function
```jsx
<button onClick={() => {
  alert('You clicked me!');
}}>
```

Functions must be passed to event handlers not called.
If functions are called rather than passed they will execute on render
```jsx
{//Correct}
<button onClick={handleClick}>
    <button onClick={() => alert('...')}>
    {//Incorrect}
        <button onClick={alert('...')}>
            <button onClick={alert('...')}>
```

Because event handlers are declared in your component you can access
component props in the handler body
Ex:
```jsx
function AlertButton({ message, children }) {
  return (
    <button onClick={() => alert(message)}>
      {children}
    </button>
  );
}
```

## Passing event handlers as props
You might need to do this to make a generic button class that can have different
onClick functions passed to it. A more specified type of button stamp can then
be made.
```jsx
function Button({ onClick, children }) {
  return (
    <button onClick={onClick}>
      {children}
    </button>
  );
}

function PlayButton({ movieName }) {
    function handlePlayClick() {
        alert(`Playing ${movieName}!`);
    }

    return (
        <Button onClick={handlePlayClick}>
            Play "{movieName}"
        </Button>
    );
}
```

Event handler props by convention begin with on. 
Ex: 
onClick 
onSmash(can be user defined not browser event)
`<button onClick={onSmash}>`

Event handlers catch events from any children your component has. Events
"bubble" or "propagate" up the tree. First where the even happened then on upwards.
Example a button within a div. If both div and button alert on click. Then when
button is pressed it will alert first and then div will.

Exception: onScroll only works on the JSX tag you attach it to.

Event handlers receive one argument `e` which is an event object.
You can stop propagaton with `e.stopPropagation`

If you have propagation problems this can be a useful pattern for debugging.
You can stop propagation before the handler.
```jsx
<button onClick={e => {
e.stopPropagation();
onClick();
}}>
```

Some browser events have default behavior associated with them. For example,
`<form>` submit happen when a button is clicked in a form. By default, it will
reload the whole page.
You can prevent behaviors like this with `e.preventDefault()`

Event handlers are the best place for side effects.
They don't need to be pure and its a good place to change something.
Changing things is done in a specific way in React through useState.





