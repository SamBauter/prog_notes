## Imperative vs Declarative
Imperative - describe every step needed to make a hawaiian pizza
Declarative - just ask for a hawaiian pizza

React is declarative and this makes it concise and simpler.
Normal JS manipulation of the DOM is more imperative and verbose.

## React stuff
Two libs:
1. react (core library)
2. react-dom (methods for using react with DOM)

```jsx
//Actually not jsx but found in  index.html file
<script type="text/jsx">
      const app = document.getElementById('app');
      const root = ReactDOM.createRoot(app);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
```

You got a syntax error: that's because your render has JSX.
Browsers don't understand JSX out of the box you'll need a compiler
like `Babel` to transform JSX code into regular JS.

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

```

## 3 JSX Rules
1. Return a single root element. If you are returning multiple elements
wrap them in a parent tag. For example a `<div></div>` 
or a _Fragment_ `<></>` which will leave no trace in the browser

2. Close all the tags! Self closing tags like `<img>` must become `<img/>`
3. camelCase almost everything. There are some reserved words like class
as a result you must use className. For example, `stroke-width` will become
`strokeWidth`.

If you already have some HTML use a converter for simple conversion.





