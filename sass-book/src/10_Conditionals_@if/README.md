# @if

In this tutorial, we will explore how to use conditionals (`@if` statements) in SASS to create dynamic and efficient stylesheets. If you have experience with other programming languages, you’ll find SASS conditionals straightforward. Let’s dive in!

## Understanding Conditionals in SASS

Conditionals in SASS allow you to execute different pieces of code based on certain conditions. This can be incredibly useful for generating styles only when specific conditions are met, thereby reducing redundant CSS and making your stylesheet more maintainable.

### Basic Syntax

The basic syntax for an `@if` statement in SASS is similar to other programming languages:

```scss
@if (condition) {
  // Code to execute if condition is true
} @else {
  // Code to execute if condition is false
}
```

Let’s start with a simple example.

### Simple Example

In your `colors.scss` file, add the following code:

```scss
@if (10 > 5) {
  .test-if {
    color: black;
  }
}
```

Here, the condition `10 > 5` is always true, so the `.test-if` class with `color: black` will be generated.

#### Testing the Conditional

To test this, open your `index.html` file and add a test element:

```html
<div class="test-if">This text should be black.</div>
```

After compiling your SASS to CSS, you should see the `.test-if` class in the CSS, and the text should appear in black.

Now, change the condition to `10 < 5`, which is false:

```scss
@if (10 < 5) {
  .test-if {
    color: black;
  }
}
```

Compile your SASS again, and you will notice that the `.test-if` class is no longer generated.

### Adding an Else Clause

You can also add an `@else` clause to handle the false condition:

```scss
@if (10 < 5) {
  .test-if {
    color: black;
  }
} @else {
  .test-if-2 {
    color: white;
  }
}
```

Now, if the condition `10 < 5` is false, the `.test-if-2` class with `color: white` will be generated instead.

### Practical Use Case: Color Utilities

Let’s apply this concept to a more practical example. Suppose we are creating a utility class for colors, and we want to avoid generating redundant variations for `black` and `white`.

Consider the following SASS code:

```scss
$colors: black, white, red, blue, green;

@each $color in $colors {
  .bg-#{$color} {
    background-color: $color;
  }

  .text-#{$color} {
    color: $color;
  }

  @if ($color != black and $color != white) {
    .bg-#{$color}-light {
      background-color: lighten($color, 20%);
    }

    .bg-#{$color}-dark {
      background-color: darken($color, 20%);
    }

    .text-#{$color}-light {
      color: lighten($color, 20%);
    }

    .text-#{$color}-dark {
      color: darken($color, 20%);
    }
  }
}
```

### Explanation

1. **Variables and Loops**: We define a list of colors and iterate over each color using the `@each` loop.
2. **General Utility Classes**: For each color, we generate basic background and text color utility classes.
3. **Conditional Variations**: We use an `@if` statement to check if the color is not `black` or `white`. If the condition is true, we generate light and dark variations.

### Testing the Color Utilities

Add the following HTML to your `index.html`:

```html
<div class="bg-red">This should have a red background.</div>
<div class="text-red">This should have red text.</div>
<div class="bg-red-light">This should have a light red background.</div>
<div class="bg-red-dark">This should have a dark red background.</div>
<div class="text-red-light">This should have light red text.</div>
<div class="text-red-dark">This should have dark red text.</div>

<div class="bg-black">This should have a black background.</div>
<div class="text-black">This should have black text.</div>
<!-- No light and dark variations for black -->

<div class="bg-white">This should have a white background.</div>
<div class="text-white">This should have white text.</div>
<!-- No light and dark variations for white -->
```

After compiling your SASS, you should see the corresponding CSS classes generated for colors other than `black` and `white`.
