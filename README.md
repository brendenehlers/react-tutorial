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
### Step 3 - Adding functionality
### Step 4 - Making a Counter component
