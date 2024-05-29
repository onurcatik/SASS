# Loops

- In this tutorial, we will explore how to use loops in SASS to generate a comprehensive set of utility classes for colors.
- By leveraging SASS maps and loops, we can efficiently create classes for text and background colors, as well as their lighter and darker variations.

## Prerequisites

Before we dive in, ensure you have the following setup:

1. A SASS compiler installed (e.g., `node-sass` or `sass`).
2. A project structure with a main SASS file and a variables file where your color palette is defined.

## Step 1: Create a Colors Map

First, let's define a map for our color palette in a `_variables.scss` file.

```scss
// _variables.scss
$colors: (
  primary: #3498db,
  secondary: #2ecc71,
  error: #e74c3c,
  info: #8e44ad,
  white: #ffffff
);
```

## Step 2: Create a Colors Partial

Create a new file named `_colors.scss` where we will generate our utility classes.

```scss
// _colors.scss
@import 'variables';

// Loop through colors map to generate text and background classes
@each $key, $val in $colors {
  // Generate text color classes
  .text-#{$key} {
    color: $val;
  }
  // Generate background color classes
  .bg-#{$key} {
    background-color: $val;
  }
}

// Generate light and dark variations
@each $key, $val in $colors {
  // Light variations
  @for $i from 1 through 9 {
    .text-#{$key}-light-#{$i} {
      color: mix(white, $val, $i * 10%);
    }
    .bg-#{$key}-light-#{$i} {
      background-color: mix(white, $val, $i * 10%);
    }
  }

  // Dark variations
  @for $i from 1 through 9 {
    .text-#{$key}-dark-#{$i} {
      color: mix(black, $val, $i * 10%);
    }
    .bg-#{$key}-dark-#{$i} {
      background-color: mix(black, $val, $i * 10%);
    }
  }
}
```

## Step 3: Import Colors Partial

In your main SASS file (e.g., `main.scss`), import the `_colors.scss` file.

```scss
// main.scss
@import 'variables';
@import 'colors';
```

## Step 4: Compile SASS

Compile your SASS to CSS using your preferred method. For example, using `sass` CLI:

```bash
sass main.scss main.css
```

## Step 5: Utilize Generated Classes in HTML

You can now use the generated classes in your HTML.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="main.css">
  <title>Color Utility Classes</title>
</head>
<body>
  <h1>Text Color Examples</h1>
  <span class="text-primary">Primary Text</span>
  <span class="text-secondary">Secondary Text</span>
  <span class="text-error">Error Text</span>
  <span class="text-info">Info Text</span>

  <h1>Background Color Examples</h1>
  <div class="bg-primary">Primary Background</div>
  <div class="bg-secondary">Secondary Background</div>
  <div class="bg-error">Error Background</div>
  <div class="bg-info">Info Background</div>

  <h1>Light and Dark Variations</h1>
  <div class="bg-primary-light-5 text-white">Primary Light 5 Background</div>
  <div class="bg-primary-dark-5 text-white">Primary Dark 5 Background</div>
</body>
</html>
```

## Explanation

1. **Maps and Loops**: We start by defining a map of colors. The `@each` loop iterates through this map to create utility classes for text and background colors.
2. **Light and Dark Variations**: Nested `@for` loops create lighter and darker variations of each color by mixing the base color with white or black, respectively.
3. **String Interpolation**: The `#{$variable}` syntax allows us to use variables in class names dynamically.

## Conclusion

By using SASS maps and loops, we can efficiently generate a comprehensive set of utility classes for colors. This approach reduces redundancy and makes it easy to expand your color palette in the future. If you add more colors to the map, the loops will automatically generate the corresponding classes.

Feel free to customize and extend this setup to fit your project's needs. Happy coding!
