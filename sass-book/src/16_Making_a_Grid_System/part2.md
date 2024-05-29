# Making a Grid System - 2

- In this tutorial, we will continue building our grid system using SASS.
- We will add functionalities for grid gaps and justifying content.
- By the end of this lesson, you'll be able to customize the spacing between grid items and control their alignment within a row.

## Setting Up Grid Gaps

First, we need to create a map of different grid gaps. This map will allow us to generate classes for each gap size.

### Step 1: Define the Grid Gaps Map

In your SASS file (let's assume it's named `_grid.scss`), define a map of grid gaps:

```scss
$grid-gaps: (
  0: 0px,
  1: 10px,
  2: 20px,
  3: 30px
);
```

### Step 2: Generate Gap Classes

Next, we will use an `@each` loop to create classes for each gap size:

```scss
// Grid gaps
@each $key, $val in $grid-gaps {
  .gap-#{$key} {
    > * {
      padding: $val;
    }
    margin-left: -$val;
    margin-right: -$val;
  }
}
```

This loop will generate classes like `.gap-0`, `.gap-1`, `.gap-2`, and `.gap-3`, which you can use to set the spacing between grid items. The padding is applied to the direct children (grid items), and negative margins are used to adjust the overall row's spacing.

### Example Usage

```html
<div class="row gap-2">
  <div class="col">Item 1</div>
  <div class="col">Item 2</div>
  <div class="col">Item 3</div>
</div>
```

This will apply a 20px gap between the items in the row.

## Justifying Content in the Grid

We also want to provide options for justifying content within a row. We'll create classes that align items to the left, right, center, or distribute space around them.

### Step 1: Define Justify Content Values

Create a list of values for the `justify-content` property:

```scss
$layout-values: flex-start, flex-end, center, space-between, space-around;
```

### Step 2: Generate Justify Classes

Use an `@each` loop to generate classes for each justify value:

```scss
// Justify content classes
@each $val in $layout-values {
  .justify-#{$val} {
    justify-content: $val;
  }
}
```

This will generate classes like `.justify-flex-start`, `.justify-flex-end`, `.justify-center`, etc.

### Example Usage

```html
<div class="row justify-center">
  <div class="col">Item 1</div>
  <div class="col">Item 2</div>
  <div class="col">Item 3</div>
</div>
```

This will center the items within the row.

## Putting It All Together

Now let's see the complete SASS code and an example HTML file.

### Complete SASS Code

```scss
$grid-gaps: (
  0: 0px,
  1: 10px,
  2: 20px,
  3: 30px
);

$layout-values: flex-start, flex-end, center, space-between, space-around;

// Grid gaps
@each $key, $val in $grid-gaps {
  .gap-#{$key} {
    > * {
      padding: $val;
    }
    margin-left: -$val;
    margin-right: -$val;
  }
}

// Justify content classes
@each $val in $layout-values {
  .justify-#{$val} {
    justify-content: $val;
  }
}
```

### Example HTML File

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Grid System Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="row gap-2 justify-center">
    <div class="col">Item 1</div>
    <div class="col">Item 2</div>
    <div class="col">Item 3</div>
  </div>
</body>
</html>
```

### Result

With the above setup:

- The `.gap-2` class applies a 20px gap between the grid items.
- The `.justify-center` class centers the grid items within the row.
