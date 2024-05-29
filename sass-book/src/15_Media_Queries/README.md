# Media Queries

## Introduction

- In this tutorial, we will dive into responsive design using SASS by creating media queries.
- We will build mixins for different breakpoints to make our styles adaptable to various screen sizes.
- This approach makes our code reusable and efficient, ultimately leading to a better user experience.

### What You Will Learn

- Creating a breakpoints map
- Defining media query mixins
- Using these mixins in your CSS

## Step-by-Step Guide

### Step 1: Create the Breakpoints File

Start by creating a new file in your SASS project. This file will contain all the media query-related code.

```scss
// File: shinobi/_breakpoints.scss
```

### Step 2: Define the Breakpoints Map

We'll define a map of breakpoints, each corresponding to a typical device width.

```scss
// File: shinobi/_breakpoints.scss

$breakpoints: (
  xs: 0,
  sm: 480px,
  md: 720px,
  lg: 960px,
  xl: 1200px
);
```

### Step 3: Create Mixins for Each Breakpoint

We will create mixins for each breakpoint to make our code modular and reusable. Each mixin will use the breakpoints defined in the map.

```scss
// File: shinobi/_breakpoints.scss

@mixin xs {
  @media (min-width: map-get($breakpoints, xs)) {
    @content;
  }
}

@mixin sm {
  @media (min-width: map-get($breakpoints, sm)) {
    @content;
  }
}

@mixin md {
  @media (min-width: map-get($breakpoints, md)) {
    @content;
  }
}

@mixin lg {
  @media (min-width: map-get($breakpoints, lg)) {
    @content;
  }
}

@mixin xl {
  @media (min-width: map-get($breakpoints, xl)) {
    @content;
  }
}
```

### Step 4: Create a Flexible Breakpoint Mixin

This mixin allows you to specify any custom breakpoint, making your media queries more flexible.

```scss
// File: shinobi/_breakpoints.scss

@mixin breakpoint($bp: 0) {
  @media (min-width: $bp) {
    @content;
  }
}
```

### Step 5: Import the Breakpoints File

To use these mixins, you need to import the breakpoints file into your main SASS file.

```scss
// File: shinobi/index.scss

@import 'breakpoints';
```

### Step 6: Using the Breakpoint Mixins

Let's test our mixins by creating a class that changes its color based on the screen width.

```scss
// File: shinobi/index.scss

.responsive-test {
  @include xs {
    color: red;
  }
  @include sm {
    color: blue;
  }
  @include md {
    color: green;
  }
  @include lg {
    color: purple;
  }
  @include xl {
    color: orange;
  }
  @include breakpoint(1400px) {
    color: pink;
  }
}
```

### Step 7: Add the Test Class to Your HTML

To see the effect of our responsive styles, add a div with the class `responsive-test` to your HTML.

```html
<!-- File: index.html -->

<div class="responsive-test">Changing Colors</div>
```

### Step 8: Test in the Browser

After saving all your changes, open the HTML file in a browser and resize the window to see the color changes based on the screen width.
