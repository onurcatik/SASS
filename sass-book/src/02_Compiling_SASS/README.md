# Compiling SASS into CSS with Gulp

- We'll start by creating a SASS file, writing some basic SASS code, and then setting up Gulp to watch and compile our SASS files.

## Step 1: Setting Up the Project

1. **Create a Project Directory**: Open VS Code and create a new project directory. Inside this directory, create an `index.html` file with the following basic structure:

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>SASS Tutorial</title>
       <link rel="stylesheet" href="css/index.css">
   </head>
   <body>
       <h1>Hello Ninjas</h1>
   </body>
   </html>
   ```
2. **Create a SASS File**: Right-click in your project directory in VS Code, select `New File`, and name it `index.scss`.

## Step 2: Writing SASS Code

Copy the following SASS code into your `index.scss` file. This includes some basic styles and a Google font import:

```scss
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

body {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

h1 {
    color: #333;
    text-align: center;
    margin-top: 50px;
}
```

## Step 3: Setting Up Gulp

### Installing Node.js and npm

Make sure you have Node.js installed. Open the terminal in VS Code and type the following command to check:

```bash
node -v
```

If you see a version number, Node.js is installed. If not, download and install it from [Node.js](https://nodejs.org/).

### Initialize npm

Run the following command to initialize npm in your project directory:

```bash
npm init -y
```

This will create a `package.json` file in your project directory.

### Installing Gulp and Plugins

Install Gulp, Gulp SASS, and SASS with the following command:

```bash
npm install gulp gulp-sass sass --save-dev
```

## Step 4: Creating the Gulp File

Create a new file named `gulpfile.js` in your project directory. Add the following code to set up Gulp:

```javascript
const { src, dest, watch, series } = require('gulp');
const sass = require('gulp-sass')(require('sass'));

// Function to compile SASS to CSS
function buildStyles() {
    return src('index.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(dest('css'));
}

// Function to watch for changes in SASS files
function watchTask() {
    watch(['index.scss'], buildStyles);
}

// Export the functions
exports.default = series(buildStyles, watchTask);
```

### Explanation:

1. **Imports**: We import the necessary functions from Gulp and the `gulp-sass` plugin.
2. **buildStyles Function**: This function specifies the source SASS file, compiles it to CSS, and outputs it to the `css` folder.
3. **watchTask Function**: This function watches the `index.scss` file for changes and re-runs the `buildStyles` function whenever a change is detected.
4. **Exports**: We export the default Gulp task, which runs `buildStyles` initially and then starts `watchTask`.

## Step 5: Running Gulp

In the terminal, run the following command to start Gulp:

```bash
gulp
```

This command will compile your SASS file to CSS and start watching for changes. If you make any changes to the `index.scss` file and save it, Gulp will automatically recompile the SASS to CSS.

## Step 6: Previewing in the Browser

To preview your changes in the browser, you can use the Live Server extension in VS Code:

1. Install the Live Server extension from the VS Code marketplace.
2. Right-click on your `index.html` file and select `Open with Live Server`.

This will open your `index.html` file in the browser and automatically reload the page whenever you make changes to your files.
