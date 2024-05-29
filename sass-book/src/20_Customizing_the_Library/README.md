# Customizing Your Own CSS Library

- In this tutorial, we'll go through the steps of integrating a pre-built CSS library into your project, customizing it with your own styles, and ensuring it updates dynamically using SASS and Gulp.

## Step 1: Setting Up Your Project

1. **Create Project Directory**: Open your project directory in a text editor like VS Code.
2. **Add CSS Library**: Drag the `shinobi` folder, which contains all the source files of the CSS library, into your project directory.

## Step 2: Creating the Gulp File

Create a `gulpfile.js` in your project directory with the following content:

```javascript
const gulp = require('gulp');
const sass = require('gulp-sass')(require('sass'));
const purgecss = require('gulp-purgecss');

gulp.task('sass', function() {
  return gulp.src('./sass/**/*.scss')
    .pipe(sass().on('error', sass.logError))
    .pipe(purgecss({
      content: ['./**/*.html']
    }))
    .pipe(gulp.dest('./css'));
});

gulp.task('watch', function() {
  gulp.watch('./sass/**/*.scss', gulp.series('sass'));
});
```

This Gulp configuration will watch for changes in the `sass` folder and recompile the SASS files while purging unused CSS classes based on your HTML content.

## Step 3: Setting Up Your Custom SASS Folder

1. **Create SASS Folder**: Create a new folder named `sass` in your project directory.
2. **Create Index SASS File**: Inside the `sass` folder, create a file named `index.scss`.

## Step 4: Importing and Customizing the CSS Library

To use and customize the CSS library, follow these steps:

### Importing the Library

Open the `index.scss` file and import the `shinobi` library:

```scss
@import '../shinobi/index';
```

### Adding Custom Styles

Now, add any custom styles or overrides. For example, to add a new class and customize the primary color:

```scss
// Custom test class
.test {
  margin: 10px;
}

// Override primary color
$primary: indigo !default;

@import '../shinobi/index';
```

### Using Default Keyword

Ensure you use the `!default` keyword to allow overriding variables. Update the `shinobi` library's variable definitions:

```scss
// shinobi/_variables.scss

$primary: blue !default;
$secondary: green !default;
$base-padding: 0.75rem !default;
$base-border-thickness: 1px !default;
```

This ensures that user-defined variables are not overwritten by the library defaults.

## Step 5: Running Gulp

Run Gulp to compile the SASS files:

```sh
gulp
```

This will compile the `index.scss` file, including your custom styles and the imported `shinobi` library styles.

## Step 6: Testing Your Customizations

Create an HTML file to test your customizations:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="css/index.css">
  <title>Test Page</title>
</head>
<body>
  <nav class="navbar-primary">Primary Navbar</nav>
  <div class="test">This is a test div with custom margin.</div>
</body>
</html>
```

Open this HTML file in your browser. If everything is set up correctly, you should see your custom styles applied.

## Customizing Further

You can further customize other variables by overriding them in your `index.scss` file:

```scss
// Custom overrides
$primary: indigo !default;
$base-padding: 1rem !default;
$base-border-thickness: 3px !default;

@import '../shinobi/index';
```

Run Gulp again:

```sh
gulp
```

Reload your HTML file in the browser to see the updated styles.
