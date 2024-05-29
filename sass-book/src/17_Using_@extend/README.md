# @extend

- In this tutorial, we will explore the `@extend` feature in SASS, which allows us to extend or inherit CSS properties from another rule.
- This is somewhat similar to using a mixin but with notable differences.
- We will demonstrate this by creating a new simple navbar component for our CSS library.

## Step 1: Setting Up the Navbar Component

First, let's create a new file called `_navbar.scss` inside the `components` folder. This file will contain the styles for our navbar component.

### Creating the `_navbar.scss` File

```scss
// _navbar.scss
.navbar {
  padding: $base-padding $base-padding * 2;
  box-shadow: $base-box-shadow;

  .site-title {
    font-size: $font-size-large;
  }
}
```

Next, we need to import this new file inside our main `index.scss` file where we consolidate all the components.

### Importing `_navbar.scss` in `index.scss`

```scss
// index.scss
@import 'components/navbar';
```

## Step 2: Defining Common Layout Styles

To make our styles more reusable, we will define a common layout rule at the top of our `_navbar.scss` file.

### Adding the Flex Layout Rule

```scss
// _navbar.scss
%flex-layout {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
}
```

## Step 3: Extending the Flex Layout in Navbar

We can use the `@extend` directive to apply the `flex-layout` properties to our `navbar` class.

### Extending Flex Layout in Navbar

```scss
// _navbar.scss
.navbar {
  @extend %flex-layout;
  padding: $base-padding $base-padding * 2;
  box-shadow: $base-box-shadow;

  .site-title {
    font-size: $font-size-large;
  }
}
```

## Step 4: Using the Navbar in HTML

Now, let's add our new navbar to an HTML file to see it in action.

### Adding Navbar in HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="styles.css">
  <title>Navbar Example</title>
</head>
<body>
  <nav class="navbar">
    <h2 class="site-title">Shinobi CSS</h2>
    <p>A lightweight CSS library for dev ninjas</p>
  </nav>
</body>
</html>
```

## Step 5: Adjusting the Layout with Containers

To ensure that the navbar content is centered, we will wrap the content in a `container` class and apply the `flex-layout` properties to it as well.

### Updating `_navbar.scss` with Container

```scss
// _navbar.scss
.navbar {
  @extend %flex-layout;
  padding: $base-padding $base-padding * 2;
  box-shadow: $base-box-shadow;

  .site-title {
    font-size: $font-size-large;
  }

  .container {
    @extend %flex-layout;
  }
}
```

### Updating HTML with Container

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="styles.css">
  <title>Navbar Example</title>
</head>
<body>
  <nav class="navbar">
    <div class="container">
      <h2 class="site-title">Shinobi CSS</h2>
      <p>A lightweight CSS library for dev ninjas</p>
    </div>
  </nav>
</body>
</html>
```

## Step 6: Using Placeholders to Avoid Unnecessary Output

We don't need the `flex-layout` class to be output in the final CSS file. We can convert it to a placeholder by replacing the dot with a percentage sign.

### Updating Placeholder in `_navbar.scss`

```scss
// _navbar.scss
%flex-layout {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
}

.navbar {
  @extend %flex-layout;
  padding: $base-padding $base-padding * 2;
  box-shadow: $base-box-shadow;

  .site-title {
    font-size: $font-size-large;
  }

  .container {
    @extend %flex-layout;
  }
}
```

## Step 7: Creating Color Variations with @each Loop

We can create different color variations for the navbar using an `@each` loop to iterate over a map of colors.

### Adding Color Variations in `_navbar.scss`

```scss
// _navbar.scss
@each $key, $val in $colors {
  .navbar-#{$key} {
    @extend .navbar;
    background-color: $val;
  }
}
```

### Using Color Variations in HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="styles.css">
  <title>Navbar Example</title>
</head>
<body>
  <nav class="navbar navbar-primary text-white">
    <div class="container">
      <h2 class="site-title">Shinobi CSS</h2>
      <p>A lightweight CSS library for dev ninjas</p>
    </div>
  </nav>
</body>
</html>
```
