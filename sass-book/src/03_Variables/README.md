# Variables

## 1. Why Use Variables in SASS?

Variables in SASS are similar to CSS variables but with a different syntax. They are particularly useful when you have values like theme colors, font sizes, or other repetitive values in your stylesheet. Instead of hardcoding these values repeatedly, you can define them once as variables and reuse them. This approach makes your code more maintainable and easier to update.

## 2. Setting Up SASS

Before we dive into the code, ensure you have SASS installed. You can install SASS globally on your machine using npm (Node Package Manager):

```bash
npm install -g sass
```

Once installed, you can compile SASS files into CSS using the following command:

```bash
sass input.scss output.css
```

## 3. Defining Variables in SASS

In SASS, variables are defined using the `$` symbol. Let's create a few variables for theme colors:

```scss
// Define theme colors
$primary: #326dfe; // Primary theme color (blue)
$secondary: #1ac89e; // Secondary theme color (green)
$error: #d32752; // Error color (red)
$info: #f6c31c; // Info color (yellow)
```

## 4. Using Variables in Selectors

You can use these variables in your CSS selectors to apply consistent styles throughout your project. Here's an example:

```scss
h1 {
  color: $primary;
}

a {
  color: $secondary;
}

button {
  color: white;
  border: 0;
  background: $primary;
}

.error {
  color: $error;
  border-color: $error;
  border-style: solid;
}

.notification {
  color: $secondary;
  border-color: $secondary;
  border-style: solid;
}
```

## 4. HTML Structure

Here's a simple HTML structure to see the effects of our SASS variables:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="output.css">
  <title>SASS Variables Example</title>
</head>
<body>
  <h1>Heading 1</h1>
  <a href="#">Link</a>
  <p class="error">Error Message</p>
  <p class="notification">Notification Message</p>
  <button>Click Me</button>
</body>
</html>
```

## 5. Advanced Variable Usage

Variables can be used for more than just colors. Let's define variables for spacing and borders:

```scss
// Define spacing and border variables
$base-padding: 0.75rem;
$base-margin: 0.75rem;
$base-border-thickness: 1px;
$base-border-radius: 20px;
```

Now, let's apply these variables to our selectors:

```scss
h1 {
  margin-bottom: $base-margin;
}

button {
  border-radius: $base-border-radius;
  padding: $base-padding;
}

.error {
  margin: $base-margin;
  padding: $base-padding;
  border-radius: $base-border-radius;
  border-width: $base-border-thickness;
}

.notification {
  margin: $base-margin;
  padding: $base-padding;
  border-radius: $base-border-radius;
  border-width: $base-border-thickness;
}
```

## 6. Compiling SASS to CSS

To see the effects of our SASS code, compile it to CSS:

```bash
sass style.scss output.css
```

Open your HTML file in a browser to see the styled elements. You should see consistent spacing, borders, and colors applied based on the variables we defined.
