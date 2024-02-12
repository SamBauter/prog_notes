# Conditional Rendering
Display different things with `if` `&&` and `?:` operators.

Ex:
```jsx
// Return an indicator like a checkmark
if (isPacked) {
  return <li className="item">{name} ✔</li>;
}
// Improved with ternary for maintainability: Use only for simple conditions.
//If things get complex consider extracting more child components out or use props. 
//Use variables and functions to tidy up complex expressions
return (
    <li className="item">
        {isPacked ? name + ' ✔' : name}
    </li>
);

// Return Nothing or in other words don't render, uncommon can surpised developers using your component.
if (isPacked) {
    return null;
}

// Render when true otherwise nothing using &&
// Returns right side if left side is truthy. If left side is falsy automatically returns left side.
    <li className="item">
        {name} {isPacked && '✔'}
    </li>
//Don't use 0 on left side of && 
Ex: messageCount && <p>New messages</p>
// left side is falsy and thus gets returned as `0` not nothing
```

Note: Common misconception JS && and short circuiting
The && operator will return the first **operand** if it is falsy without evaluating the second **operand**.
It returns the **operand** not `false`!
Sometimes you need to booleanize the lhs to not render Ex:`messageCount > 0 && <p>New messages</p>` will render nothing.

Note if the shortcuts get in the way of writing plain code trying using an `if` with a variable. This
is the most verbos but also the most flexible f:or complex logic.
```jsx
let itemContent = name;
if (isPacked) {
    itemContent = name + " ✔";
}
<li className="item">
    {itemContent}
</li>

```

