---
title: how to create some sort of random image roulette app Red88
date: 2023-03-06 21:27:24
categories:
- Game
tags:
---


# How to Create a Random Image Roulette App: Red88

Are you looking for a fun new way to engage your audience or create an interactive experience? One option to consider is a random image roulette app, such as Red88. With this app, users can upload a set of images which are then displayed randomly on the screen, creating a game-like atmosphere.

In this article, we’ll be walking through the process of creating a basic version of a random image roulette app using HTML, CSS, and JavaScript. Let’s get started!

## Step 1: Setting Up the HTML & CSS

First, we’ll set up the basic structure of our app using HTML and CSS. We’ll create a container element for the images and buttons, as well as separate elements for each image, which will be hidden by default.

```html
<div class="container">
  <div class="images">
    <img src="img/image1.jpg">
    <img src="img/image2.jpg">
    <img src="img/image3.jpg">
    <img src="img/image4.jpg">
    <img src="img/image5.jpg">
  </div>
  <button class="btn">Spin</button>
</div>
```

```css
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.images img {
  display: none;
}
```

Next, we’ll add some basic styling to make things look nicer. We’ll create a border around the image container, and style the button.

```css
.container {
  border: 2px solid black;
  padding: 10px;
  border-radius: 5px;
}

.btn {
  background-color: #4CAF50;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  border-radius: 5px;
  cursor: pointer;
}
```

## Step 2: Adding JS Functionality

Now that we’ve got the basic structure and styling in place, it’s time to add some functionality using JavaScript. First, we’ll define an array of our image sources, and create a function to randomly select one of them.

```javascript
const images = [
  'img/image1.jpg',
  'img/image2.jpg',
  'img/image3.jpg',
  'img/image4.jpg',
  'img/image5.jpg'
];

function getRandomImage() {
  const randomIndex = Math.floor(Math.random() * images.length);
  return images[randomIndex];
}
```

Next, we’ll create another function to handle the spin button click event. This function will hide the current image (if there is one), randomly select a new one, and display it on the screen.

```javascript
const imagesContainer = document.querySelector('.images');
const imagesArray = Array.from(imagesContainer.children);

let currentImage = null;

function spin() {
  if (currentImage) {
    currentImage.style.display = 'none';
  }
  const newImageSrc = getRandomImage();
  currentImage = imagesArray.find(img => img.src.endsWith(newImageSrc));
  currentImage.style.display = 'block';
}

const spinButton = document.querySelector('.btn');
spinButton.addEventListener('click', spin);
```

Finally, we’ll add some finishing touches. We’ll set the initial image to be randomly selected when the page loads, and add a loading spinner to indicate that the app is loading the images.

```javascript
function showLoadingSpinner() {
  const spinner = document.createElement('div');
  spinner.classList.add('spinner');
  imagesContainer.appendChild(spinner);
}

function hideLoadingSpinner() {
  const spinner = document.querySelector('.spinner');
  spinner.remove();
}

function init() {
  showLoadingSpinner();
  const randomImage = getRandomImage();
  const firstImage = imagesArray.find(img => img.src.endsWith(randomImage));
  firstImage.style.display = 'block';
  hideLoadingSpinner();
}

window.addEventListener('load', init);
```

```css
.spinner {
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #4CAF50;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: spin 1s linear infinite;
  margin: auto;
}

@keyframes spin {
  to {transform: rotate(360deg);}
}
```

And that’s it! With just a few lines of HTML, CSS, and JavaScript, we’ve created a simple but functional random image roulette app. Of course, there are many ways to customize this app to make it more interesting and engaging, such as adding sound effects, keeping track of scores, or allowing users to upload their own images.

We hope this tutorial has been helpful in getting you started with creating your own random image roulette apps. Happy coding!