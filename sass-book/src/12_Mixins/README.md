# Mixins

- In this tutorial, we'll explore one of the powerful features in SASS called mixins.
- Mixins allow us to group CSS properties and values that we can reuse across different CSS rules.
- This is particularly useful when we have multiple elements sharing common styles, saving us from writing repetitive code.

## What Are Mixins?

Mixins in SASS are like functions in programming languages. They encapsulate a set of CSS properties and values, which can then be included in other selectors. This makes our stylesheets more maintainable and DRY (Don't Repeat Yourself).

## Example: Button Component

We'll create a button component that demonstrates how to use mixins effectively. This component will include buttons with different styles such as primary, secondary, and outlined.

### Step 1: Setting Up the Environment

First, ensure you have a SASS setup. Create a new file for the button component in your `components` folder named `_button.scss`.

```scss
// components/_button.scss
```

### Step 2: Define Color Variables

We assume you have a color map defined in your variables file. It might look something like this:

```scss
// styles/_variables.scss
$colors: (
  "primary": #007bff,
  "secondary": #6c757d,
  "error": #dc3545,
  "info": #17a2b8,
);

$base-padding: 10px;
$base-border-radius: 5px;
```

### Step 3: Create Button Styles Using Mixins

Let's create our button component with mixins.

1. **Loop Through Colors**: Generate button classes for each color.
2. **Define Common Styles**: Use a mixin to group common properties.
3. **Apply Mixins**: Include the mixin in each button class and customize as needed.

```scss
// components/_button.scss

// Define a mixin for common button styles
@mixin btn($bg-color) {
  text-decoration: none;
  cursor: pointer;
  display: inline-block;
  border: none;
  padding: $base-padding $base-padding * 2;
  border-radius: $base-border-radius;
  background-color: $bg-color;
}

// Loop through the color map and generate button classes
@each $key, $val in $colors {
  .btn-#{$key} {
    @include btn($val);
  }

  .btn-outlined-#{$key} {
    @include btn(#fff); // Default background for outlined buttons is white
    border: 2px solid $val; // Add a border of the color
    background-color: #fff; // Override background color to white
  }
}

// Generic button class
.btn {
  @include btn(#e2e2e2); // Default light gray background
}

// Hover effects
@each $key, $val in $colors {
  .btn-#{$key}:hover {
    background-color: lighten($val, 5%);
  }

  .btn-outlined-#{$key}:hover {
    background-color: $val;
    color: #fff; // Assuming text should be white on hover
  }
}
```

### Step 4: Include the Button Component in Your Main Stylesheet

Ensure you include the button styles in your main stylesheet.

```scss
// styles/main.scss
@import 'variables';
@import 'components/button';
```

### Step 5: HTML Markup for Buttons

Add some HTML to see your buttons in action.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="styles/main.css">
  <title>SASS Buttons</title>
</head>
<body>
  <a href="#" class="btn">Default Button</a>
  <a href="#" class="btn-primary">Primary Button</a>
  <a href="#" class="btn-secondary">Secondary Button</a>
  <a href="#" class="btn-error">Error Button</a>
  <a href="#" class="btn-info">Info Button</a>
  <a href="#" class="btn-outlined-primary">Outlined Primary</a>
  <a href="#" class="btn-outlined-secondary">Outlined Secondary</a>
  <a href="#" class="btn-outlined-error">Outlined Error</a>
  <a href="#" class="btn-outlined-info">Outlined Info</a>
</body>
</html>
```

### Step 6: Preview in Browser

After saving your changes, open the HTML file in your browser. You should see a set of styled buttons, including default, primary, secondary, and outlined variants. Hover over the buttons to see the hover effects in action.
