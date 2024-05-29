# Using the CSS Library

- In this tutorial, we'll demonstrate how to use the CSS library we've built with SASS in a simple homepage for a dummy website.
- We'll break down the HTML structure, use the compiled CSS library, and ensure the website is styled correctly.
- By the end of this tutorial, you'll have a functional and styled webpage using the custom CSS classes and utilities from our library.

## Setting Up the HTML File

First, let's create an `index.html` file and set up the basic structure. This file will link to our compiled CSS library and include several sections to showcase various components and utilities.

### 1. HTML Boilerplate

Create a new HTML file and add the following boilerplate:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dummy Website</title>
    <link rel="stylesheet" href="path/to/your/compiled/css/library.css">
</head>
<body>
    <!-- Content will be added here -->
</body>
</html>
```

Replace `path/to/your/compiled/css/library.css` with the actual path to your compiled CSS file.

### 2. Adding the Navbar

Let's start by adding a navigation bar at the top of our page. We use the `navbar` class we created in previous lessons.

```html
<nav class="navbar">
    <div class="container">
        <h1 class="site-title">My Website</h1>
        <ul class="display-f">
            <li class="ml-1"><a href="#work" class="text-hover-secondary">Work</a></li>
            <li class="ml-1"><a href="#about" class="text-hover-secondary">About</a></li>
        </ul>
    </div>
</nav>
```

### 3. Adding the Intro Section

Next, we'll add an intro section with a heading, a paragraph, and a button.

```html
<section class="intro">
    <div class="container mt-5">
        <div class="row justify-center">
            <div class="col-12-xs col-5-md">
                <h2 class="font-xxxl">Black Belt</h2>
                <h3 class="font-xxxl text-secondary">Your Website</h3>
                <p class="text-gray mt-1 mb-2">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam.</p>
                <a href="#work" class="btn btn-outline-secondary text-secondary text-hover-white">See Our Work</a>
            </div>
            <div class="col-12-xs col-5-md">
                <img src="images/laptop.svg" alt="Laptop" class="img-responsive">
            </div>
        </div>
    </div>
</section>
```

### 4. Adding the About Section

Now, let's add an about section.

```html
<section id="about" class="bg-secondary-light-9 mt-5 pt-3 pb-3">
    <div class="container">
        <h2 class="mb-2">About Shinobi Designs</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam.</p>
        <p class="mb-3">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam.</p>
    </div>
</section>
```

### 5. Adding the Work Section

The work section will display several items in a grid layout.

```html
<section id="work" class="mt-5 mb-5">
    <div class="container">
        <h2 class="mb-2">Some of Our Work</h2>
        <div class="row gap-2">
            <div class="col-12-xs col-6-md col-3-lg">
                <div class="card no-padding">
                    <h3 class="card-title m-1">Project 1</h3>
                    <img src="images/food.jpg" alt="Food" class="img-responsive">
                    <p class="m-1">Lorem ipsum dolor sit amet.</p>
                </div>
            </div>
            <div class="col-12-xs col-6-md col-3-lg">
                <div class="card no-padding">
                    <h3 class="card-title m-1">Project 2</h3>
                    <img src="images/mario.jpg" alt="Mario" class="img-responsive">
                    <p class="m-1">Lorem ipsum dolor sit amet.</p>
                </div>
            </div>
            <div class="col-12-xs col-6-md col-3-lg">
                <div class="card no-padding">
                    <h3 class="card-title m-1">Project 3</h3>
                    <img src="images/marmite.jpg" alt="Marmite" class="img-responsive">
                    <p class="m-1">Lorem ipsum dolor sit amet.</p>
                </div>
            </div>
            <div class="col-12-xs col-6-md col-3-lg">
                <div class="card no-padding">
                    <h3 class="card-title m-1">Project 4</h3>
                    <img src="images/notes.jpg" alt="Notes" class="img-responsive">
                    <p class="m-1">Lorem ipsum dolor sit amet.</p>
                </div>
            </div>
        </div>
        <div class="row justify-center mt-3">
            <a href="#contact" class="btn btn-primary">Contact Us</a>
        </div>
    </div>
</section>
```

### 6. Adding the Footer

Finally, let's add a simple footer.

```html
<footer class="bg-gray-light-9 pt-3 pb-3 mt-5">
    <div class="container">
        <p>© 2024 Shinobi Designs. All rights reserved.</p>
    </div>
</footer>
```

## Adding Images

Ensure you have the following images in your `images` directory:

- `laptop.svg`
- `food.jpg`
- `mario.jpg`
- `marmite.jpg`
- `notes.jpg`

These images will be displayed in the relevant sections of our website.

## Final Preview

With all the sections added, your `index.html` should look like this:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dummy Website</title>
    <link rel="stylesheet" href="path/to/your/compiled/css/library.css">
</head>
<body>
    <nav class="navbar">
        <div class="container">
            <h1 class="site-title">My Website</h1>
            <ul class="display-f">
                <li class="ml-1"><a href="#work" class="text-hover-secondary">Work</a></li>
                <li class="ml-1"><a href="#about" class="text-hover-secondary">About</a></li>
            </ul>
        </div>
    </nav>

    <section class="intro">
        <div class="container mt-5">
            <div class="row justify-center">
                <div class="col-12-xs col-5-md">
                    <h2 class="font-xxxl">Black Belt</h2>
                    <h3 class="font-xxxl text-secondary">Your Website</h3>
                    <p class="text-gray mt-1 mb-2">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam.</p>
                    <a href="#work" class="btn btn-outline-secondary text-secondary text-hover-white">See Our Work</a>
                </div>
                <div class="col-12-xs col-5-md">
                    <img src="images/laptop.svg" alt="Laptop" class="img-responsive">
                </div>
            </div>
        </div>
    </section>

    <section id="about" class="bg-secondary-light-9 mt-5 pt-3 pb-3">
        <div class="container">
            <h2 class="mb-2">About Shinobi Designs</h2>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam.</p>
            <p class="mb-3">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam.</p>
        </div>
    </section>

    <section id="work" class="mt-5 mb-5">
        <div class="container">
            <h2 class="mb-2">Some of Our Work</h2>
            <div class="row gap-2">
                <div class="col-12-xs col-6-md col-3-lg">
                    <div class="card no-padding">
                        <h3 class="card-title m-1">Project 1</h3>
                        <img src="images/food.jpg" alt="Food" class="img-responsive">
                        <p class="m-1">Lorem ipsum dolor sit amet.</p>
                    </div>
                </div>
                <div class

="col-12-xs col-6-md col-3-lg">
                    <div class="card no-padding">
                        <h3 class="card-title m-1">Project 2</h3>
                        <img src="images/mario.jpg" alt="Mario" class="img-responsive">
                        <p class="m-1">Lorem ipsum dolor sit amet.</p>
                    </div>
                </div>
                <div class="col-12-xs col-6-md col-3-lg">
                    <div class="card no-padding">
                        <h3 class="card-title m-1">Project 3</h3>
                        <img src="images/marmite.jpg" alt="Marmite" class="img-responsive">
                        <p class="m-1">Lorem ipsum dolor sit amet.</p>
                    </div>
                </div>
                <div class="col-12-xs col-6-md col-3-lg">
                    <div class="card no-padding">
                        <h3 class="card-title m-1">Project 4</h3>
                        <img src="images/notes.jpg" alt="Notes" class="img-responsive">
                        <p class="m-1">Lorem ipsum dolor sit amet.</p>
                    </div>
                </div>
            </div>
            <div class="row justify-center mt-3">
                <a href="#contact" class="btn btn-primary">Contact Us</a>
            </div>
        </div>
    </section>

    <footer class="bg-gray-light-9 pt-3 pb-3 mt-5">
        <div class="container">
            <p>© 2024 Shinobi Designs. All rights reserved.</p>
        </div>
    </footer>
</body>
</html>
```
