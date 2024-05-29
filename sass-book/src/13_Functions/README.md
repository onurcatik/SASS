# Functions

- In this tutorial, we will dive into creating custom functions in SASS to enhance our CSS capabilities.
- Functions in SASS allow us to encapsulate reusable pieces of logic that return single values, which we can then use in our styles.
- This is different from mix-ins, which group together multiple properties. Let's explore how to create and use a custom function in SASS.

## Step 1: Setting Up the Project Structure

Firstly, ensure you have a proper directory structure for your SASS files. For this example, we'll be working with the following structure:

```
/shinobi
    |_ _functions.scss
    |_ _buttons.scss
    |_ main.scss
```

## Step 2: Creating the Custom Function

Let's start by creating a custom function that returns a complementary and lightened color for a given input color.

1. Create a `_functions.scss` file inside the `shinobi` folder.
2. Define the function `light-comp`:

```scss
// _functions.scss

@function light-comp($color) {
    // Get the complementary color
    $complement: complement($color);

    // Lighten the complementary color by 30%
    $light-complement: lighten($complement, 30%);

    // Return the lightened complementary color
    @return $light-complement;
}
```

## Step 3: Importing the Function in Your Main SASS File

To use this function, you need to import the `_functions.scss` file into your main SASS file.

```scss
// main.scss

@import 'shinobi/functions';
@import 'shinobi/buttons';
```

## Step 4: Using the Function in Your Styles

Now, let's create a new variant for our buttons that uses this function. Update the `_buttons.scss` file to include the new button style.

```scss
// _buttons.scss

// Define colors (assuming these are defined somewhere in your project)
$primary-color: #3498db;
$secondary-color: #2ecc71;
$color-map: (
    'primary': $primary-color,
    'secondary': $secondary-color,
    // Add other colors as needed
);

.button {
    // Common button styles
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    transition-duration: 0.4s;
}

.button-primary {
    background-color: map-get($color-map, 'primary');
    color: white;
}

.button-secondary {
    background-color: map-get($color-map, 'secondary');
    color: white;
}

// New complement button variant
.button-complement-primary {
    @include button(map-get($color-map, 'primary'));
    color: light-comp(map-get($color-map, 'primary'));

    &:hover {
        background-color: light-comp(map-get($color-map, 'primary'));
        color: map-get($color-map, 'primary');
    }
}

.button-complement-secondary {
    @include button(map-get($color-map, 'secondary'));
    color: light-comp(map-get($color-map, 'secondary'));

    &:hover {
        background-color: light-comp(map-get($color-map, 'secondary'));
        color: map-get($color-map, 'secondary');
    }
}
```

## Step 5: Using the Buttons in HTML

Finally, add the new button classes to your HTML to see the result.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="path/to/compiled/css/main.css">
    <title>SASS Functions Example</title>
</head>
<body>
    <button class="button button-complement-primary">Primary Complement</button>
    <button class="button button-complement-secondary">Secondary Complement</button>
</body>
</html>
```

## Step 6: Compiling Your SASS

Compile your SASS files to CSS using a SASS compiler. If you are using the command line, you can run:

```bash
sass shinobi/main.scss path/to/compiled/css/main.css
```
