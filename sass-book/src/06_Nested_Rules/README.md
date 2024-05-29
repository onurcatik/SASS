# Nested Rules

- In this tutorial, we will explore the power of nesting CSS rules using SASS (Syntactically Awesome Style Sheets).
- By the end of this tutorial, you'll understand how to create a reusable card component with nested CSS rules, making your code more organized and easier to maintain.

## Step 1: Setting Up the Project

First, ensure you have a project structure similar to the following:

```
my-sass-library/
├── components/
│   ├── _card.scss
├── styles/
│   ├── _variables.scss
│   ├── index.scss
├── index.html
```

## Step 2: Defining Variables

Before creating the card component, we need to define some SASS variables for consistent styling across the project. Open the `_variables.scss` file and add the following:

```scss
// _variables.scss

$base-box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
$base-font-size: 16px;
$base-padding: 16px;
$base-border-thickness: 1px;
```

These variables will be used in the card component for styling purposes.

## Step 3: Creating the Card Component

Next, create the `_card.scss` file inside the `components` folder. This file will contain the SASS code for our card component.

### Basic Card Structure

Start by defining the basic structure and styles for the card:

```scss
// _card.scss

.card {
  display: block;
  padding: $base-padding;
  border: $base-border-thickness solid #ddd;
  box-shadow: $base-box-shadow;
}
```

### Nesting Rules

Now, let's nest the rules for different elements inside the card component, such as the title and body:

```scss
// _card.scss

.card {
  display: block;
  padding: $base-padding;
  border: $base-border-thickness solid #ddd;
  box-shadow: $base-box-shadow;

  .card-title {
    font-size: $base-font-size;
    padding-bottom: $base-padding;
    font-weight: bold;
  }

  .card-body {
    font-size: $base-font-size;

    a {
      text-decoration: underline;
    }
  }
}
```

By nesting the rules, we make our SASS code cleaner and more readable.

## Step 4: Importing the Card Component

To ensure that the card component's styles are included in our final CSS, we need to import the `_card.scss` file into our main `index.scss` file.

```scss
// index.scss

@import 'variables';
@import 'components/card';
```

## Step 5: Using the Card Component

Now that we have defined and imported the card component, let's use it in our HTML file. Open the `index.html` file and add the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SASS Library</title>
  <link rel="stylesheet" href="styles/index.css">
</head>
<body>
  <h2>Cards</h2>
  <div class="card">
    <h1 class="card-title">This is a card title</h1>
    <p class="card-body">Lorem ipsum dolor sit amet, consectetur adipiscing elit. <a href="#">Read more</a></p>
  </div>
</body>
</html>
```

This code creates a card component with a title and body, including a link inside the body.

## Step 6: Compiling SASS to CSS

To see the changes in the browser, we need to compile the SASS code into CSS. You can use a SASS compiler like `node-sass` or `sass` (Dart implementation).

Run the following command to compile the SASS code:

```bash
sass styles/index.scss styles/index.css
```

## Step 7: Viewing the Result

Open `index.html` in your browser. You should see a card component styled according to the rules defined in `_card.scss`. If the card stretches the full width of the page, you can temporarily adjust its width using the browser's developer tools.

### Example Adjustments in Developer Tools

```css
.card {
  margin: 30px;
  max-width: 400px;
}
```

These adjustments will be formalized later when we add more features to our CSS library, such as a grid system or layout containers.
