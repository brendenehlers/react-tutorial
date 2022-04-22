# React Tutorial
This is a tutorial in setting up a basic counter app using React functional components and hooks.  This is designed to be refresher or a crash course, not the full package for people learning to use React.  Simply, it a stepping stone in the learning process.

## Steps

### Step 1 - Setting up the environment
Prerequisites: npm, yarn, git installed on your machine, and a code editor of your choice (I recommend VS Code)
This step concerns the setup of the development environment in which we will be working. 

First, you will need to clone this repo onto your local machine using the `git clone` syntax in your terminal.  Open a terminal (command line on Windows) and navigate to the place where you want the project to be stored (I like ~/Documents/Projects but it's personal preference).  Once there, run 
```
git clone https://github.com/brendenehlers/react-tutorial
``` 
to bring the repo from github to your local machine.  When the clone finishes, navigate into the resulting folder using `cd react-tutorial`.

Now, the project has been stored on your local machine but is just the code that was uploaded to github.  Since JavaScript uses a lot of packages to build on what others have already made, we need to install said packages.  If you look in `package.json`, you will see an entry entitled 'dependences'.  These are the packages that the author has added to the project.  But we just have the reference to the package and the version, not the package itself.  Therefore, we need to install them.  That can be done by running `yarn install` in a terminal currently located in the project directory.  After this process has finished, there will be a folder called 'node_modules' which contains all the data for the packages referred to in the 'dependencies'.

Once you have 'node_modules', you can run `yarn run start` to run the development version of this app.  After a few seconds, your terminal will say 'Compiled Successfully!', and a browser will pop-up and bring you to `localhost:3000`, which is just the words 'Hello, World' in the top left of the screen.  If this happens, then you know you setup the environment correctly!

### Step 2 - Basic UI setup
This step will teach you some very basic JSX and how we can change the code in `App.jsx` to make the UI for a simple counter app.

First, open the file `App.jsx`.  Notice this is not a '.js' file, instead it is a '.jsx' file.  Normal '.js' files will not allow you to use JSX syntax.    This is a very simple React functional component.  A functional component is simply a JavaScript function that returns JSX object.  Functional components can get very complicated, but that is beyond the scope of this tutorial.  Notice on line 3, there is the "Hello, World" that we see on the website.  Try changing the "Hello, World" to "Goodbye, World" and save the file.  Notice that the website automatically updates.  This makes developing much easier.

Okay, now we're going to implement some basic UI to the app.  First, replace `<p>Hello, World</p>` on line 3 with `<div></div>`, then navigate to between the two tags and press return (enter on Windows).  Your App function should now look like this:
```
function App() {
    return <div>

    </div>
}
```
Within in the div tag, add the following 3 lines:
`<button>-</button>`
`<span>0</span>`
`<button>+</button>`
such that the App function now looks like this:
```
function App() {
    return <div>
        <button>-</button>
        <span>0</span>
        <button>+</button>
    </div>
}
```
This is a very basic UI setup for a counter app.  If you're like me and cannot stand the elements being that close to one another, you can add `style={{display: 'flex', gap: '5px'}}` to the div tag to space the elements out a little more, but that is not required.  The resulting App function will look like this:
```
function App() {
    return <div style={{display: 'flex', gap: '5px'}}>
        <button>-</button>
        <span>0</span>
        <button>+</button>
    </div>
}
```
And that's the basic setup! We will add the functionality to the button in the next step using functions and hooks!

### Step 3 - Adding functionality
In this step we add the functionality to the counter.  This will allow the user to increment the value by pressing the '+' and decrement the value by pressing the '-' button.

First, we need to setup the variable that will represent the value within the code.  We will use the react component state to do this.  In a functional component like the one we're using, we need to use the `useState` hook that is built into React.  Hook functions allow us to "hook" into React lifecycle methods, allow us to use their functionality within a functional component.  Other hooks include `useEffect`, `useReducer`, and `useMemo`.  More info about hooks can be found [here](https://reactjs.org/docs/hooks-reference.html).  

To include the `useState` in your function, you need to import it from the React library by adding the following line to line 1 of the `App.jsx` file.
```
import { useState } from 'react'
```
This allows us to include the `useState` function in our app.

The basic setup of the `useState` function is as follows:
```
const [value, setValue] = useState(defaultValue)
```
where the `value` and `setValue` are the getter and setter, resp. and the `defaultValue` is the initial value.  The names of `value` and `setValue` are up to the user, but the convention is to have the second term be 'use' plus the name of the first value.  

For our app, we're going to use the descriptive variable names of `count` and `setCount`.  Create a new line between the function declaration for App and teh return.  Then, add the following line in the new space:
```
const [count, useCount] = useState(0)
```
This creates a new variable `count` that we can reference to get the current value, and an setter function `setCount` that we can use to set the `count` variable.  We set the initial value of `count` to 0, but this can be any number you would like.

Now that we have the variable to represent the count, we need to add the functionality to change that variable.  First, we'll start by adding a representation of the value to the rendered HTML.  To do this, we need to replace the 0 within the `<span>` tag with the count variable.  In React, this is a simple process.  Simple replace `<span>0</span>` with `<span>{count}</span>`.  Note the curly braces around the variable.  Those allow us to put plain js within the JSX elements.  Your return statement should now look like this:
```
return <div style={{display: 'flex', gap: '5px'}}>
    <button>-</button>
    <span>{count}</span>
    <button>+</button>
</div>
```

Now that we have the value represented in the JSX return, we need to add the `increment` and `decrement` functions.  These functions are very simple and similar, all they do is either increase the value by 1 or decrease the value by 1.  The functions are coded as follows:
```
function increment() {
    setCount(count+1)
}
function decrement() {
    setCount(count-1)
}
```
Since the `setCount` function sets the value of `count` we don't need to assign anything to count.  We will add those functions between the line containing `const [count, setCount] = useState(0)` and the return statement.  As such, the App function will now look like this:
```
function App() {
    const [count, setCount] = useState(0)

    function increment() {
        setCount(count+1)
    }
    
    function decrement() {
        setCount(count-1)
    }

    return <div style={{display: 'flex', gap: '5px'}}>
        <button>-</button>
        <span>{count}</span>
        <button>+</button>
    </div>
}
```

Now we need to change the buttons to use the new `increment` and `decrement` buttons.  To do this, we simply add the tag `onClick` to the buttons.  Note the C in click is uppercase, unlike the traditional HTML tag `onclick`.  This is because React uses `onclick` internally and needs to differentiate between the two different tags.  In the case of the '+' button, it will change from `<button>+</button` to `<button onClick={increment}>+</button>`.  The '-' button will change in the same way, but with the `decrement` function.  Now, the `App` function will look like this:
```
function App() {
    const [count, setCount] = useState(0)

    function increment() {
        setCount(count+1)
    }

    function decrement() {
        setCount(count-1)
    }

    return <div style={{display: 'flex', gap: '5px'}}>
        <button onClick={decrement}>-</button>
        <span>{count}</span>
        <button onClick={increment}>+</button>
    </div>
}
```

And now, the counter will increment by 1 when you press the '+' button and decrement by 1 when you press the '-' button!

### Step 4 - Making a Counter component
