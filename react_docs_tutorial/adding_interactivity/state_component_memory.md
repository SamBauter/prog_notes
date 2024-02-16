# State a components memory
Components change what is on the screen as a result of interaction.

Two Reasons for special state variables:
1. Local variables don’t persist between renders. 
When React renders this component a second time, it renders it from scratch—it doesn’t 
consider any changes to the local variables.
2. Changes to local variables won’t trigger renders. 
React doesn’t realize it needs to render the component again with the new data.

Syntax:
```jsx
const [index, setIndex] = useState(0);
```

## Hooks
- Special functions that are only available while react is rendering.
- React hooks start with "use"

Can only be called at the top level of your components. Cannot call inside conditions,
loops, or other nested functions.

## Use State
Use state only takes one argument `useState(initialValue)`
and it produces a `state variable` ex: `index`
and a `state setter function` ex: `setIndex`

Usually you will use both the `state var` and the `state setter` in conjunction
to make a new value by operating on the previous value
Ex: 
```jsx
function handleNextClick() {
    setIndex(index + 1);
  }
```

Use multiple `state vars` if their state is unrelated.
In a form you might want to group many fields into a single state var obj more on that later.

State is isolated and private. It is local to the component instance on the screen.
If you rendered the same component twice they would each have their own individual states.

The parent component cannot change state it is fully private to the component declaring it. This
makes it easier to change it without impacting other components.

Don't introduce state variables if you don't need to keep information between re-renders.
Within a single event handler a regular variable is often fine.


