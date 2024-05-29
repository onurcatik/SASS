# Partials & @import

- In this tutorial, we'll explore how to manage large SASS files using partials and the `@import` directive.
- This approach helps keep your SASS code modular, easier to maintain, and more readable.

## Introduction to Partials

- As your SASS codebase grows, keeping all the code in a single file can become unmanageable.
- Partials allow you to split your code into multiple smaller files, each responsible for different aspects of your CSS.
- For example, you can have separate files for variables, mixins, resets, buttons, links, and colors.
- These partial files can then be imported into a main SASS file.

## Setting Up Partials

Let's start by creating a partial for variables.

### Create a Partial File for Variables

Create a new file named `_variables.scss`. The underscore prefix indicates that this is a partial file, which SASS will not compile into a standalone CSS file.

```scss
// _variables.scss
$primary-color: #3498db;
$secondary-color: #2ecc71;
$font-stack: Helvetica, sans-serif;
```

### Move Variables from Main File to Partial

Move any variables from your main SASS file (`styles.scss`) to `_variables.scss`.

```scss
// styles.scss (Before)
$primary-color: #3498db;
$secondary-color: #2ecc71;
$font-stack: Helvetica, sans-serif;

body {
    font-family: $font-stack;
    color: $primary-color;
}
```

After moving variables to `_variables.scss`:

```scss
// styles.scss (After)
@import 'variables';

body {
    font-family: $font-stack;
    color: $primary-color;
}
```

### Import the Partial in Your Main File

Use the `@import` directive to import the `_variables.scss` partial into your main SASS file.

```scss
// styles.scss
@import 'variables';

body {
    font-family: $font-stack;
    color: $primary-color;
}
```

## Working with Partials and Build Tools

When using build tools like Gulp to compile SASS, you might encounter issues where the partial files get compiled into standalone CSS files. Let's handle this correctly.

### Gulp Task for SASS Compilation

Here's an example Gulp task to compile SASS files:

```javascript
const gulp = require('gulp');
const sass = require('gulp-sass')(require('sass'));

gulp.task('sass', function() {
    return gulp.src('src/scss/**/*.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(gulp.dest('dist/css'));
});

gulp.task('watch', function() {
    gulp.watch('src/scss/**/*.scss', gulp.series('sass'));
});

gulp.task('default', gulp.series('sass', 'watch'));
```

In the above configuration, the `gulp.src('src/scss/**/*.scss')` line matches all `.scss` files, including partials. This can lead to undesired standalone CSS files for partials.

### Prevent Partial Compilation

Rename your partials with an underscore prefix. For example, `_variables.scss` instead of `variables.scss`. This tells the SASS compiler to ignore these files when compiling standalone CSS files.

```plaintext
src/
└── scss/
    ├── _variables.scss
    └── styles.scss
```

Now, update the `gulp.src` pattern to avoid unnecessary partial compilation:

```javascript
gulp.task('sass', function() {
    return gulp.src('src/scss/styles.scss') // Only compile the main file
        .pipe(sass().on('error', sass.logError))
        .pipe(gulp.dest('dist/css'));
});
```

## Building a Project Structure

Let's create a structured project with multiple partials:

### Create Directory Structure

Organize your SASS files into a meaningful structure:

```plaintext
src/
└── scss/
    ├── base/
    │   ├── _reset.scss
    │   └── _typography.scss
    ├── components/
    │   ├── _buttons.scss
    │   └── _links.scss
    ├── layout/
    │   ├── _header.scss
    │   └── _footer.scss
    ├── utils/
    │   ├── _variables.scss
    │   ├── _mixins.scss
    │   └── _functions.scss
    └── styles.scss
```

### Use Partials in Main File

Import all partials into your main `styles.scss` file:

```scss
// styles.scss
@import 'utils/variables';
@import 'utils/mixins';
@import 'utils/functions';
@import 'base/reset';
@import 'base/typography';
@import 'components/buttons';
@import 'components/links';
@import 'layout/header';
@import 'layout/footer';
```

### Example Partial Content

Here's an example of what your partial files might look like:

**_reset.scss**

```scss
// _reset.scss
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

**_buttons.scss**

```scss
// _buttons.scss
.btn {
    background-color: $primary-color;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}
```
