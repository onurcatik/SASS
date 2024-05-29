# Introduction

- In this series, we'll explore what SASS is, why it's beneficial, and how to use it to create a CSS library.
- This introduction will set the stage for the upcoming lessons by covering the basics and prerequisites needed to get started with SASS.

## What is SASS?

- SASS (Syntactically Awesome Stylesheets) is an extension of CSS that introduces programming-like features, making it more powerful and flexible.
- It's often described as "CSS on steroids" because it brings functionalities like variables, loops, functions, and inheritance to CSS.

### Benefits of Using SASS

- **Variables**: Store reusable values like colors, fonts, or any CSS value.
- **Nesting**: Nest CSS selectors in a way that follows the same visual hierarchy of your HTML.
- **Partials and Import**: Split your CSS into smaller, maintainable files.
- **Mixins**: Create reusable chunks of CSS code.
- **Inheritance**: Share a set of CSS properties from one selector to another.
- **Functions**: Write reusable CSS code with optional parameters.

### Why Use SASS?

- SASS simplifies writing complex CSS and is widely used in the development community.
- Many popular CSS frameworks like Bootstrap and Bulma are built using SASS.
- In this tutorial, we'll create a mini CSS library similar to Bootstrap or Tailwind using SASS, which you can use in your projects to speed up development.

## Setting Up Your Environment

### Step 1: Install Node.js

To compile SASS into CSS, we'll use a task runner called Gulp, which requires Node.js. Follow these steps to install Node.js:

1. Go to [nodejs.org](https://nodejs.org/).
2. Click the download button to get the latest version of Node.js.
3. Follow the installation steps, keeping the default settings.

### Step 2: Install Gulp

Once Node.js is installed, you can install Gulp using npm (Node Package Manager).

1. Open your terminal or command prompt.
2. Run the following command to install Gulp globally:
   ```bash
   npm install --global gulp-cli
   ```

### Step 3: Create a Project Directory

Create a new directory for your project and navigate into it:

```bash
mkdir sass-project
cd sass-project
```

### Step 4: Initialize a New Node.js Project

Initialize a new Node.js project by running:

```bash
npm init -y
```

This will create a `package.json` file in your project directory.

### Step 5: Install Gulp Locally

Install Gulp and necessary plugins locally in your project:

```bash
npm install --save-dev gulp gulp-sass
```

## Creating Your First SASS File

### Step 1: Create a `src` Directory

Create a `src` directory to store your SASS files:

```bash
mkdir src
```

### Step 2: Create a SASS File

Inside the `src` directory, create a file named `style.scss` and add some SASS code:

```scss
// src/style.scss
$primary-color: #3498db;

body {
  font-family: Arial, sans-serif;
  background-color: $primary-color;
  color: white;

  h1 {
    font-size: 2em;
  }

  p {
    font-size: 1.2em;
  }
}
```

### Step 3: Create a Gulp File

In your project root, create a `gulpfile.js` to define Gulp tasks:

```javascript
// gulpfile.js
const gulp = require('gulp');
const sass = require('gulp-sass')(require('sass'));

gulp.task('sass', function() {
  return gulp.src('src/*.scss')
    .pipe(sass().on('error', sass.logError))
    .pipe(gulp.dest('dist/css'));
});

gulp.task('watch', function() {
  gulp.watch('src/*.scss', gulp.series('sass'));
});

gulp.task('default', gulp.series('sass', 'watch'));
```

### Step 4: Run Gulp

Run Gulp to compile your SASS to CSS and watch for changes:

```bash
gulp
```

This will create a `dist/css` directory with a compiled `style.css` file.

### Step 5: Link CSS in HTML

Create an HTML file to use the compiled CSS:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="dist/css/style.css">
  <title>SASS Project</title>
</head>
<body>
  <h1>Welcome to SASS</h1>
  <p>This is a paragraph styled with SASS.</p>
</body>
</html>
```
