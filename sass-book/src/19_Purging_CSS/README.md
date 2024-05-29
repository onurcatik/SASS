# Purging CSS to Optimize Your CSS Library

- In this tutorial, we will learn how to purge unused CSS to keep our CSS files small and optimized for production.
- By the end of this tutorial, you'll be able to set up a workflow where any unused CSS rules are automatically removed from your final CSS file.

## Step 1: Install `gulp-purgecss` Plugin

First, we need to install the `gulp-purgecss` plugin. Open your terminal and run the following command:

```sh
npm install gulp-purgecss --save-dev
```

This will add `gulp-purgecss` to your development dependencies.

## Step 2: Update Your `gulpfile.js`

Now, let's update our `gulpfile.js` to include the `gulp-purgecss` plugin.

1. **Require the `gulp-purgecss` Plugin:**

   At the top of your `gulpfile.js`, add the following line to require the plugin:

   ```javascript
   const purgecss = require('gulp-purgecss');
   ```
2. **Integrate `gulp-purgecss` into Your Build Process:**

   Find your `buildStyles` function in the `gulpfile.js` and update it to include `gulp-purgecss`. Your function should look something like this:

   ```javascript
   function buildStyles() {
       return src('src/scss/**/*.scss')  // Adjust the path as needed
           .pipe(sass().on('error', sass.logError))
           .pipe(purgecss({
               content: ['*.html']
           }))
           .pipe(dest('dist/css'));
   }
   ```

   This code snippet tells `gulp-purgecss` to look at all HTML files in the root directory to determine which CSS rules are used.
3. **Watch HTML Files for Changes:**

   To ensure that changes in your HTML files trigger a rebuild of the CSS, update your watch task as follows:

   ```javascript
   function watchFiles() {
       watch('src/scss/**/*.scss', buildStyles);
       watch('*.html', buildStyles);
   }
   ```

   This will ensure that whenever you change an HTML file, the CSS will be purged and rebuilt.

## Step 3: Run Gulp and Check Results

1. **Cancel any running Gulp process:**

   If you have an existing Gulp process running, cancel it (usually with `Ctrl+C` in your terminal).
2. **Run Gulp:**

   Start Gulp again to see the changes:

   ```sh
   gulp
   ```
3. **Check the Output:**

   After running Gulp, check the `dist/css` directory. Open the generated CSS file and notice that it should be significantly smaller. This is because `gulp-purgecss` has removed all unused CSS rules.

## Step 4: Verify Dynamic Changes

To verify that dynamic changes in your HTML are correctly reflected in the purged CSS:

1. **Modify Your HTML:**

   Open an HTML file and add a class that wasn't used before, e.g., `navbar-secondary`.

   ```html
   <div class="navbar-secondary">Secondary Navbar</div>
   ```
2. **Save and Check:**

   Save the HTML file and check the generated CSS file to see if the new class `navbar-secondary` is included.

   ```sh
   grep 'navbar-secondary' dist/css/*.css
   ```

   You should find the `navbar-secondary` class in the CSS file.
3. **Remove or Change Classes:**

   Change the class in your HTML to `navbar-primary` and save the file again. Check the CSS file to ensure that `navbar-secondary` is removed and `navbar-primary` is included.

   ```html
   <div class="navbar-primary">Primary Navbar</div>
   ```

   ```sh
   grep 'navbar-primary' dist/css/*.css
   ```

   The `navbar-primary` class should now be present in the CSS file, and `navbar-secondary` should be purged.

## Step 5: Final

- By following these steps, you have successfully integrated `gulp-purgecss` into your workflow.
- This will help you keep your CSS files small and optimized by removing any unused styles, leading to faster load times and a better user experience.

Here's the final `gulpfile.js` for reference:

```javascript
const { src, dest, watch, series } = require('gulp');
const sass = require('gulp-sass')(require('sass'));
const purgecss = require('gulp-purgecss');

function buildStyles() {
    return src('src/scss/**/*.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(purgecss({
            content: ['*.html']
        }))
        .pipe(dest('dist/css'));
}

function watchFiles() {
    watch('src/scss/**/*.scss', buildStyles);
    watch('*.html', buildStyles);
}

exports.default = series(buildStyles, watchFiles);
```
