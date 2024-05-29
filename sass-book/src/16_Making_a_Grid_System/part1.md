# Making a Grid System - 1

- In this tutorial, we will build a grid system for our CSS library using SASS.
- This grid system is inspired by popular frameworks like Bootstrap, and it will help you create flexible, responsive layouts with ease.

## Step-by-Step Guide

### Step 1: Create the Grid SCSS File

First, let's create a new file inside our `shinobi` folder called `_grid.scss`. This file will contain all the styles related to our grid system.

```scss
// shinobi/_grid.scss
```

### Step 2: Define the Grid Columns Variable

We will define a variable `grid-columns` that specifies the number of columns in our grid. A 12-column grid is a popular choice, but you can change this number as needed.

```scss
$grid-columns: 12;
```

### Step 3: Import the Math Package

To perform calculations for our grid, we need to use the math package provided by SASS.

```scss
@use "sass:math";
```

### Step 4: Create Base Layout Classes

We will start by creating some base layout classes, namely `.container` and `.row`.

#### Container Class

The `.container` class centers your content on the page and restricts its maximum width.

```scss
.container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
    box-sizing: border-box;
}
```

#### Row Class

The `.row` class will be used to hold our grid columns and will utilize Flexbox.

```scss
.row {
    display: flex;
    flex-flow: row wrap;
}
```

### Step 5: Create Column Classes

Now we will create the column classes for different breakpoints. These classes will be dynamically generated using a loop and the mixins we created in the last tutorial.

#### Extra Small Columns

We start with the `extra-small` mixin.

```scss
@include extra-small {
    @for $i from 1 through $grid-columns {
        .col-#{$i}-extra-small {
            box-sizing: border-box;
            flex-grow: 0;
            width: math.div($i * 100, $grid-columns) * 1%;
        }
    }
}
```

This loop generates classes like `.col-1-extra-small`, `.col-2-extra-small`, etc., each setting the width proportionally.

### Step 6: Generate Column Classes for All Breakpoints

We will now generate similar classes for all breakpoints: small, medium, large, and extra-large.

```scss
@include extra-small {
    @for $i from 1 through $grid-columns {
        .col-#{$i}-extra-small {
            box-sizing: border-box;
            flex-grow: 0;
            width: math.div($i * 100, $grid-columns) * 1%;
        }
    }
}

@include small {
    @for $i from 1 through $grid-columns {
        .col-#{$i}-sm {
            box-sizing: border-box;
            flex-grow: 0;
            width: math.div($i * 100, $grid-columns) * 1%;
        }
    }
}

@include medium {
    @for $i from 1 through $grid-columns {
        .col-#{$i}-md {
            box-sizing: border-box;
            flex-grow: 0;
            width: math.div($i * 100, $grid-columns) * 1%;
        }
    }
}

@include large {
    @for $i from 1 through $grid-columns {
        .col-#{$i}-lg {
            box-sizing: border-box;
            flex-grow: 0;
            width: math.div($i * 100, $grid-columns) * 1%;
        }
    }
}

@include extra-large {
    @for $i from 1 through $grid-columns {
        .col-#{$i}-xl {
            box-sizing: border-box;
            flex-grow: 0;
            width: math.div($i * 100, $grid-columns) * 1%;
        }
    }
}
```

### Step 7: Import the Grid SCSS File

Don't forget to import the `_grid.scss` file in your main SCSS file.

```scss
@import 'grid';
```

### Step 8: Use the Grid System in HTML

Now that we have our grid system set up, let's use it in our HTML template.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grid System</title>
    <link rel="stylesheet" href="path/to/your/css">
</head>
<body>
    <div class="container">
        <h2 class="mb-2">Grid System</h2>
        <div class="row">
            <div class="col-12-extra-small col-5-sm col-3-xl">
                <div class="card">
                    <h3 class="card-title">Hello Ninjas</h3>
                    <p class="card-body">Lorem ipsum dolor sit amet.</p>
                </div>
            </div>
            <!-- Repeat similar structure for more columns -->
        </div>
    </div>
</body>
</html>
```
