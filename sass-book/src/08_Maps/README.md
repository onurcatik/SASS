# Maps

- In this tutorial, we'll explore how to use maps in SASS. Maps in SASS are similar to associative arrays in other programming languages or objects in JavaScript.
- They allow us to store key-value pairs, which can be incredibly useful for generating utility classes, managing color palettes, and more.
- We'll learn how to create maps, retrieve values from them, and manipulate them using various SASS functions.

## Creating a Map

Maps in SASS are created using parentheses, and key-value pairs are separated by commas. Let's start by creating a color palette map:

```scss
// Define theme colors
$primary: #3498db;
$secondary: #2ecc71;
$error: #e74c3c;
$info: #8e44ad;

// Comment indicating the start of color palettes
// Color palettes
$colors: (
  primary: $primary,
  secondary: $secondary,
  error: $error,
  info: $info,
  blue: #3498db,
  red: #e74c3c,
  yellow: #f1c40f,
  green: #2ecc71,
  orange: #e67e22,
  purple: #9900ff,
  gray: #95a5a6,
  black: black,
  white: white
);
```

## Retrieving Values from a Map

To get a value from a map, we use the `map-get` function. This function takes the map and the key as arguments and returns the corresponding value.

```scss
// Using map-get to retrieve a value
@debug map-get($colors, purple); // Output: #9900ff
```

## Checking for a Key in a Map

We can check if a map contains a specific key using the `map-has-key` function. This function returns `true` if the key exists in the map and `false` otherwise.

```scss
// Check if the map has a specific key
@debug map-has-key($colors, secondary); // Output: true
@debug map-has-key($colors, tertiary);  // Output: false
```

## Removing a Key from a Map

To remove a key from a map, we use the `map-remove` function. This function returns a new map with the specified key removed.

```scss
// Remove a key from the map
@debug map-remove($colors, primary); // Output: map without the primary key
```

## Adding a Key to a Map

To add a key to a map, we use the `map-merge` function. This function merges two maps together, with the second map's keys overwriting those in the first map if they overlap.

```scss
// Add a new key to the map
@debug map-merge($colors, (pink: #ffc0cb)); // Output: map with the new pink key
```

## Using Maps in Selectors

Maps can be used directly in CSS selectors. For example, we can use `map-get` to set the background color of a button.

```scss
// Example usage in a selector
.test-btn {
  background-color: map-get($colors, purple);
}
```

This sets the background color of `.test-btn` to the value associated with the `purple` key in the `$colors` map.

## Practical Example: Creating Utility Classes

In the next lesson, we'll see how to loop through a map to generate utility classes for each color. For now, let's summarize what we've learned about maps in SASS.

- **Creating a Map**: Use parentheses and key-value pairs.
- **Retrieving Values**: Use `map-get($map, $key)`.
- **Checking Keys**: Use `map-has-key($map, $key)`.
- **Removing Keys**: Use `map-remove($map, $key)`.
- **Adding Keys**: Use `map-merge($map1, $map2)`.

Maps are a powerful feature in SASS that allow for organized, maintainable code, especially when dealing with large sets of related variables such as colors. In the next lesson, we'll delve deeper into using maps to generate dynamic CSS classes efficiently.
