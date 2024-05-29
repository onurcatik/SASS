# Project Structure

- In this tutorial, we will build a mini CSS library similar to Bootstrap, Tailwind, or Bulma.
- Our goal is to create a simplified version of these libraries and then use it to design a web page.
- We will start by setting up a structured project to keep our SASS files organized, making it easier to update our project in the future.

## Project Structure Setup

### Step 1: Create the Project Folder

First, create a folder for your project. Let's call this folder `shinobi` as we are building a CSS library named "Shinobi CSS".

1. Create a new folder named `shinobi`.
2. Move your existing SASS files (`variables.scss` and `index.scss`) into this folder.

### Step 2: Organize SASS Files

We will organize our SASS files into partials and import them into our main `index.scss` file.

1. Create a new partial file named `_base.scss` inside the `shinobi` folder.
2. Move all the base styles, including font imports, from `index.scss` to `_base.scss`.

```scss
// shinobi/_base.scss
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

// Add other base styles here...
```

3. In `index.scss`, import the `_base.scss` file.

```scss
// shinobi/index.scss
@import 'variables';
@import 'base';

// Other styles...
```

### Step 3: Update Gulp Configuration

Ensure that Gulp watches the correct directory for SASS files.

1. Open your `gulpfile.js` and update the source and watch paths.

```javascript
const gulp = require('gulp');
const sass = require('gulp-sass')(require('sass'));

// Source and destination paths
const sassFiles = 'shinobi/**/*.scss';
const cssDest = 'dist/css';

// Compile SASS to CSS
gulp.task('sass', function() {
  return gulp.src(sassFiles)
    .pipe(sass().on('error', sass.logError))
    .pipe(gulp.dest(cssDest));
});

// Watch SASS files for changes
gulp.task('watch', function() {
  gulp.watch(sassFiles, gulp.series('sass'));
});

// Default task
gulp.task('default', gulp.series('sass', 'watch'));
```

### Step 4: Restart Gulp

Restart Gulp to ensure it watches the new directory structure.

```bash
# In your terminal
gulp
```

### Step 5: Maintain Import Order

The order in which you import your partials in `index.scss` matters. Files should be imported in the order they depend on each other.

```scss
// shinobi/index.scss

// Variables and functions should be at the top
@import 'variables';

// Base and layout styles
@import 'base';

// Colors
@import 'colors';

// Components (buttons, cards, etc.)
@import 'components';

// Utilities (margins, paddings, etc.)
@import 'utilities';
```

### Step 6: Create Partial Files

Create additional partial files as needed, following the import order.

#### Example: `_variables.scss`

```scss
// shinobi/_variables.scss
$primary-color: #3498db;
$secondary-color: #2ecc71;

// Other variables...
```

#### Example: `_colors.scss`

```scss
// shinobi/_colors.scss
.text-primary {
  color: $primary-color;
}

.bg-primary {
  background-color: $primary-color;
}

// Other color utilities...
```

#### Example: `_components.scss`

```scss
// shinobi/_components.scss
.button {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 0.25rem;
  background-color: $primary-color;
  color: white;
  cursor: pointer;
}

.button-secondary {
  background-color: $secondary-color;
}

// Other components...
```

#### Example: `_utilities.scss`

```scss
// shinobi/_utilities.scss
.m-1 {
  margin: 0.25rem;
}

.p-1 {
  padding: 0.25rem;
}

// Other utility classes...
```
