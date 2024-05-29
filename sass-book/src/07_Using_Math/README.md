# Using Math

- In this tutorial, we'll explore the use of mathematical operations in SASS to create flexible and dynamic styles.
- By leveraging multiplication, division, and other mathematical functions, we can efficiently manage values and ensure consistency throughout our CSS.
- We'll also cover debugging techniques to help you verify and troubleshoot your SASS code.

## Setting Up Your Project

First, ensure you have SASS installed in your project. If you haven't set it up yet, you can install it using npm:

```bash
npm install -g sass
```

Create a new SASS file (e.g., `styles.scss`) where you'll write your SASS code.

## Using Math for Font Sizes

We often need different font sizes for various elements. Instead of manually defining each size, we can use mathematical operations to calculate them based on a base font size. Let's start with defining a base font size and creating variations.

### Defining Font Sizes with Multiplication

1. **Define the Base Font Size:**

```scss
$base-font-size: 1rem;
```

2. **Create Variations:**

```scss
$font-size-sm: $base-font-size * 0.75;
$font-size-lg: $base-font-size * 1.5;
$font-size-xl: $base-font-size * 2;
$font-size-xxl: $base-font-size * 3;
```

3. **Using the Font Sizes:**

```scss
.card-title {
  font-size: $font-size-lg;
}
```

By defining these variables, any change to `$base-font-size` will automatically update all the variations.

## Using Division for Border Radius

Let's use division to calculate a border radius for a card component.

1. **Define the Base Border Radius:**

```scss
$base-border-radius: 20px;
```

2. **Calculate the New Border Radius Using Division:**

To avoid SASS's warning when dividing, we'll use the `math.div` function from the math module.

3. **Import the Math Module:**

```scss
@use "sass:math";
```

4. **Calculate the Border Radius:**

```scss
$border-radius-sm: math.div($base-border-radius, 4);
```

5. **Using the Border Radius:**

```scss
.card {
  border-radius: $border-radius-sm;
}
```

## Debugging SASS Code

Debugging is essential to ensure our calculations and logic are correct. SASS provides the `@debug` directive for this purpose.

### Example of Debugging

1. **Simple Debug Message:**

```scss
@debug "Hello Ninjas";
```

2. **Debugging Calculations:**

```scss
@debug math.div(10, 3);
@debug math.floor(2.6);
@debug math.max(1px, 20px, 15px, 12px);
```

### Output

When you save your SASS file, the compiler will output debug messages in the console, helping you verify the values.

```bash
Debug: Hello Ninjas
Debug: 3.3333333333333335
Debug: 2
Debug: 20px
```

## Complete Example

Here's a complete example that includes all the concepts we've discussed:

```scss
@use "sass:math";

// Base variables
$base-font-size: 1rem;
$base-border-radius: 20px;

// Font size variations
$font-size-sm: $base-font-size * 0.75;
$font-size-lg: $base-font-size * 1.5;
$font-size-xl: $base-font-size * 2;
$font-size-xxl: $base-font-size * 3;

// Border radius calculation
$border-radius-sm: math.div($base-border-radius, 4);

// Applying styles
.card {
  border-radius: $border-radius-sm;
}

.card-title {
  font-size: $font-size-lg;
}

// Debugging
@debug "Hello Ninjas";
@debug math.div(10, 3);
@debug math.floor(2.6);
@debug math.max(1px, 20px, 15px, 12px);
```
