The sales pitch for React Components is they offer a way to have interactivity while
still looking just like a markup html page.
```jsx
<PageLayout> //Full page made up of components.
  <NavigationHeader>
    <SearchBar />
    <Link to="/docs">Docs</Link>
  </NavigationHeader>
  <Sidebar />
  <PageContent>
    <TableOfContents />
    <DocumentationText />
  </PageContent>
</PageLayout>
```

How to define a component:
```jsx
    export default function Profile(){ //FUNCTION FOR COMPONENT MUST START WITH CAPITAL LETTER
    return ( //multiline returns require nesting in () otherwise only return the value on the 
        //line with return
    <img
        src = "https://i.imgur/com/blah.jpg"
        alt = "Katherine Johnson"
    />
    )
}
```

Once you have defined a component you can use it in other components jsx:
```jsx
    export default function Gallery() {
    return (
        <section>
            <h1>Amazing scientists</h1>
            <Profile /> //Notice the TitleCase
            <Profile />
            <Profile />
        </section>
        );
}
```

Components can be nested by you should not nest their definitions.
```jsx
export default function Gallery() {
  // 🔴 Never define a component inside another component!
  function Profile() {
    // ...
  }
  // ...
}
```

What is generally the root component file that contains everything?
App.js

You can only have one default export. When importing a named export it is slightly different.
```jsx
import { Profile } from './Gallery.js'; // Name export style
import Gallery from './Gallery'; // default export style
```
