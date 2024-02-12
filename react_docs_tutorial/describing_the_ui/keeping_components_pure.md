# Keeping components pure

Pure functions:
1. Same inputs same outputs. 
2. Does not change state

Components shouldn't reference any variables outside of their definition
as those variables might change breaking rule 1.

In many scenarios prefer to pass necessary variables that a component needs to
use as props.

You cannot expect your components to be rendered in any particular order.
Each component calculates its JSX on its own.
React has a "Strict Mode" where it will call each component function twice
in order to help you find components that are impure.

**Pure functions don't mutate variables outside of function scope.**

You are totally free and fine to mutate variables created within function scope.

Side effects usually belong inside `event handlers`.
These are defined inside your component but don't run during rendering.
Thus they do not need to be pure.

If you cannot find the right event handler, you can use `useEffect` call in your
component. This tells your component to execute it later AFTER rendering when
side effects are allowed. **This should be a LAST resort**




