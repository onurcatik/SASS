# Parent Selectors

- In this tutorial, we'll delve into using parent selectors in SASS to create variations of classes that include effects like hover and other pseudo-selectors such as nth-child, active, visited, or last-child.
- This will enable us to manage and style our components more effectively by leveraging SASS's powerful capabilities.

## Introduction to Parent Selectors

Parent selectors in SASS allow you to reference the parent element and apply pseudo-classes or pseudo-elements to it. This is particularly useful for creating variations of classes that apply styles under certain conditions, like when an element is hovered over.

## Setting Up

First, ensure you have SASS installed. If not, you can install it globally using npm:

```bash
npm install -g sass
```

## Example Structure

Let's start with a basic project structure:

```
project/
├── scss/
│   ├── _colors.scss
│   ├── styles.scss
├── index.html
```

### _colors.scss

In the `_colors.scss` file, we define our color variables and loop through them to generate classes.

```scss
// _colors.scss

$colors: (
  "primary": #3498db,
  "secondary": #2ecc71,
  "purple": #9b59b6,
  // Add more colors as needed
);

@each $name, $color in $colors {
  .text-#{$name} {
    color: $color;
  }
}
```

### Using Parent Selectors

We want to extend these classes to handle hover effects and other pseudo-selectors. Here's how we can do it using parent selectors:

```scss
// styles.scss

@import 'colors';

@each $name, $color in $colors {
  .text-#{$name} {
    color: $color;

    &:hover {
      color: lighten($color, 20%);
    }
  }
}
```

In the above code:

- `&:hover` references the parent class (`.text-#{$name}`) and applies the hover pseudo-class to it.
- `lighten($color, 20%)` lightens the color by 20% when hovered.

### HTML Structure

To see the effect, let's create a simple HTML file:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SASS Tutorial</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p class="text-primary">Hover over this text to see the primary color effect.</p>
  <p class="text-secondary">Hover over this text to see the secondary color effect.</p>
  <p class="text-purple">Hover over this text to see the purple color effect.</p>
</body>
</html>
```

### Compiling SASS

Compile your SASS to CSS using the following command:

```bash
sass scss/styles.scss styles.css
```

### Extending to Other Pseudo-Classes

You can further extend this to other pseudo-classes like `nth-child`, `last-child`, etc.:

```scss
@each $name, $color in $colors {
  .text-#{$name} {
    color: $color;

    &:hover {
      color: lighten($color, 20%);
    }

    &:last-child {
      color: darken($color, 20%);
    }

    &:nth-child(2) {
      color: saturate($color, 20%);
    }
  }
}
```

### Applying Light and Dark Variations

We can also create light and dark variations by mixing the colors with white or black:

```scss
@each $name, $color in $colors {
  @for $i from 1 through 9 {
    .text-hover-#{$name}-light-#{$i} {
      &:hover {
        color: mix(white, $color, $i * 10%);
      }
    }
    .text-hover-#{$name}-dark-#{$i} {
      &:hover {
        color: mix(black, $color, $i * 10%);
      }
    }
  }
}
```

### Using the New Classes

Add these new classes to your HTML to see the effects:

```html
<!-- index.html -->
<p class="text-primary text-hover-primary-light-3">Hover over this text to see the light variation effect.</p>
<p class="text-secondary text-hover-secondary-dark-5">Hover over this text to see the dark variation effect.</p>
```

### Full Code for SCSS

Here's the complete SCSS code combining everything:

```scss
// _colors.scss

$colors: (
  "primary": #3498db,
  "secondary": #2ecc71,
  "purple": #9b59b6,
  // Add more colors as needed
);

// styles.scss

@import 'colors';

@each $name, $color in $colors {
  .text-#{$name} {
    color: $color;

    &:hover {
      color: lighten($color, 20%);
    }

    &:last-child {
      color: darken($color, 20%);
    }

    &:nth-child(2) {
      color: saturate($color, 20%);
    }
  }

  @for $i from 1 through 9 {
    .text-hover-#{$name}-light-#{$i} {
      &:hover {
        color: mix(white, $color, $i * 10%);
      }
    }
    .text-hover-#{$name}-dark-#{$i} {
      &:hover {
        color: mix(black, $color, $i * 10%);
      }
    }
  }
}
```
