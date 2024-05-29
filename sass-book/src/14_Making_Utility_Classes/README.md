# Building Utility Classes for Your CSS Library

- In this tutorial, we'll create utility classes for a CSS library using SASS.
- Utility classes are reusable CSS classes that can be used to style elements consistently and quickly.
- These classes often follow a specific naming convention to apply styles like margins, paddings, opacity, etc., in a predictable manner.

We'll create a map of utility classes, iterate through it, and generate the corresponding CSS. This approach is inspired by popular CSS frameworks like Bootstrap.

## Step 1: Setting Up the Environment

First, create a new SASS file for the utility classes. This will be where we define and generate all our utility classes.

1. Create a new file named `_utilities.scss` inside your `shinobi` folder.
2. Import this file into your main SASS file (e.g., `main.scss`).

```scss
// main.scss
@import 'utilities';
```

## Step 2: Defining the Utilities Map

In the `_utilities.scss` file, start by importing the SASS math module. This will be useful for calculations.

```scss
// _utilities.scss
@use 'sass:math';

$utilities: (
  padding: (
    prefix: 'p',
    values: (
      0: 0,
      1: 1rem,
      2: 2rem,
      3: 4rem,
      4: 8rem,
      5: 16rem
    )
  ),
  padding-left: (
    prefix: 'pl',
    values: (
      0: 0,
      1: 1rem,
      2: 2rem,
      3: 4rem,
      4: 8rem,
      5: 16rem
    )
  ),
  margin: (
    prefix: 'm',
    values: (
      0: 0,
      1: 1rem,
      2: 2rem,
      3: 4rem,
      4: 8rem,
      5: 16rem
    )
  ),
  // Add more utilities as needed
);
```

Here, we define a `$utilities` map with nested maps for different types of utilities like `padding`, `padding-left`, and `margin`. Each nested map includes a `prefix` for the class name and `values` for the different strengths.

## Step 3: Generating Utility Classes

Next, we'll write SASS code to iterate through the `$utilities` map and generate the corresponding utility classes.

```scss
@each $property, $utility in $utilities {
  $prefix: map-get($utility, prefix);
  $values: map-get($utility, values);

  @each $key, $value in $values {
    .#{$prefix}-#{$key} {
      #{$property}: #{$value};
    }
  }
}
```

This code does the following:

1. Iterates through each utility in the `$utilities` map.
2. Extracts the `prefix` and `values` for each utility.
3. Iterates through the `values` and generates classes with the appropriate property and value.

## Step 4: Adding More Utilities

You can extend the `$utilities` map to include more properties, such as `opacity`, `border-radius`, `display`, etc. Here's an extended version of the map:

```scss
$utilities: (
  padding: (
    prefix: 'p',
    values: (
      0: 0,
      1: 1rem,
      2: 2rem,
      3: 4rem,
      4: 8rem,
      5: 16rem
    )
  ),
  padding-left: (
    prefix: 'pl',
    values: (
      0: 0,
      1: 1rem,
      2: 2rem,
      3: 4rem,
      4: 8rem,
      5: 16rem
    )
  ),
  margin: (
    prefix: 'm',
    values: (
      0: 0,
      1: 1rem,
      2: 2rem,
      3: 4rem,
      4: 8rem,
      5: 16rem
    )
  ),
  opacity: (
    prefix: 'o',
    values: (
      10: 0.1,
      20: 0.2,
      30: 0.3,
      40: 0.4,
      50: 0.5,
      60: 0.6,
      70: 0.7,
      80: 0.8,
      90: 0.9,
      100: 1
    )
  ),
  border-radius: (
    prefix: 'br',
    values: (
      default: 0.25rem,
      none: 0,
      xs: math.div(0.25rem, 4),
      sm: math.div(0.25rem, 2),
      lg: math.mul(0.25rem, 2),
      full: 50%
    )
  ),
  display: (
    prefix: 'd',
    values: (
      n: none,
      b: block,
      f: flex,
      'i-b': inline-block,
      'i': inline
    )
  ),
  font-size: (
    prefix: 'font',
    values: (
      sm: 0.875rem,
      md: 1rem,
      lg: 1.25rem,
      xl: 1.5rem,
      xxl: 2rem
    )
  )
);
```

## Step 5: Using the Utility Classes

Once the utility classes are generated, you can use them in your HTML files.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="styles.css">
  <title>Utility Classes</title>
</head>
<body>
  <h2 class="m-b-2">Heading with Margin Bottom</h2>
  <div class="font-sm">Small Font Size</div>
  <div class="font-md">Medium Font Size</div>
  <div class="font-lg">Large Font Size</div>
  <div class="font-xl">Extra Large Font Size</div>
  <div class="font-xxl">Extra Extra Large Font Size</div>
  <hr class="m-t-4 m-b-4">
</body>
</html>
```

In this HTML example:

- The `h2` element has a bottom margin with a strength of 2.
- The `div` elements demonstrate different font sizes.
- The `hr` elements have top and bottom margins with a strength of 4.
