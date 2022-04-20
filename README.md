# React Tutorial
This is a tutorial in setting up a basic counter app using React functional components and hooks.  This is designed to be refresher or a crash course, not the full package for people learning to use React.  Simply, it a stepping stone in the learning process.

## Steps

### Step 1 - Setting up the environment
Prerequisites: npm, yarn, git installed on your machine, and a code editor of your choice (I recommend VS Code)
This step concerns the setup of the development environment in which we will be working. 

First, you will need to clone this repo onto your local machine using the `git clone` syntax in your terminal.  Open a terminal (command line on Windows) and navigate to the place where you want the project to be stored (I like ~/Documents/Projects but it's personal preference).  Once there, run ```git clone https://github.com/brendenehlers/react-tutorial``` to bring the repo from github to your local machine.  When the clone finishes, navigate into the resulting folder using `cd react-tutorial`.

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
### Step 4 - Making a Counter component
