# Extending Your CSS Library

- In this tutorial, we'll extend our custom CSS library, "Shinobi," by adding a new component called `badge`.
- By the end of this guide, you'll know how to create and customize badges, a common UI element used to display notifications or counts, and incorporate them into your project.

## Step 1: Creating the Badge Component

First, we'll create a new SASS file for our badge component. We'll call this file `badges.scss`.

### badges.scss

```scss
@use 'sass:math';

@mixin badge($background-color: $info-color) {
  border-radius: math.round($base-border-radius * 4px);
  background-color: $background-color;
  padding: math.div($base-padding, 4) math.div($base-padding, 2);
  font-size: $font-size-small;
  font-weight: normal;
}

.badge {
  @include badge;
}

@each $key, $value in $colors {
  .badge-#{$key} {
    @include badge($value);
  }
}
```

### Explanation

1. **Mixin Definition**: We define a mixin called `badge` that accepts a `$background-color` parameter. By default, it uses the `$info-color`.
2. **Styles**:

   - `border-radius`: Uses the base border radius, multiplied by 4.
   - `background-color`: Set to the passed background color.
   - `padding`: Calculated using the base padding divided by 4 for vertical padding and 2 for horizontal padding.
   - `font-size` and `font-weight`: Set to small font size and normal weight respectively.
3. **Default Badge Class**: The `.badge` class includes the `badge` mixin with default settings.
4. **Color Variations**: Using the `@each` loop, we create color variations for the badge by iterating over the `$colors` map and generating classes like `.badge-primary`, `.badge-secondary`, etc.

## Step 2: Importing the Badge Component

Next, we need to import our new `badges.scss` file into our main SASS file to ensure it's compiled.

### index.scss

```scss
// Other imports...
@import 'badges';
```

Ensure this import statement is added towards the end of your `index.scss` file.

## Step 3: Using the Badge Component in HTML

Now, let's add a badge to our HTML to see it in action.

### index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="path/to/compiled/css">
  <title>Shinobi CSS Library</title>
</head>
<body>
  <section class="work">
    <h3>
      Work
      <span class="badge badge-orange" style="margin-left: 8px;">New</span>
    </h3>
    <!-- Other content -->
  </section>

  <script src="path/to/compiled/js"></script>
</body>
</html>
```

### Explanation

- **Badge Element**: We use a `<span>` element with the class `badge badge-orange`. This applies the default badge styles and the orange color variation.
- **Styling**: An inline style adds a left margin to separate the badge from the adjacent text.

## Step 4: Compiling and Viewing the Badge

Make sure your SASS is being compiled correctly. If you encounter issues, try making a small change in your SASS file to force recompilation.

Once compiled, open your HTML file in a browser (using a live server or any method you prefer) to see the badge in action.

### Example Output

You should see a badge next to the "Work" heading, styled with the defined SASS styles and in the specified orange color.
