# Frontend Mentor - Product preview card component solution

This is a solution to the [Product preview card component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/product-preview-card-component-GO7UmttRfa).
## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
    - [Desktop](#desktop)
    - [Desktop (active states)](#desktop-active-states)
    - [Mobile (~375 pixels width)](#mobile-375-pixels-width)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
    - [The HTML stuff](#the-html-stuff)
    - [The CSS stuff](#the-css-stuff)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout depending on their device's screen size
- See hover and focus states for interactive elements

### Screenshot

#### Desktop
<div align="center"><img src="./screenshots/screenshot-desktop.png" width="320" /></div>

#### Desktop (active states)
<div align="center"><img src="./screenshots/screenshot-desktop-active.png" width="320" /></div>

#### Mobile (~375 pixels width)
<div align="center"><img src="./screenshots/screenshot-mobile.png" width="320" /></div>

### Links

- Live Site URL: [https://oczywsziysya-fem-04.netlify.app](https://oczywsziysya-fem-04.netlify.app)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Responsive images

### What I learned

I learned about some HTML attributes and CSS properties that come in handy when dealing with images in general. 

#### The HTML stuff

* **\[HTML `<img>` attribute\] width/height** - These are just size hints. Even if we choose to deal with image sizing through CSS properties, if we previously know the "base-size" of an image, it's a good practice to indicate it in the HTML inside the `<img>` tag. Why? Because that way the browser will know how much space should be reserved to that image even if it hasn't loaded yet. This prevents sudden text jumps on the page when the image finishes loading. Also, **these attributes' values should be unitless**: you shouldn't write `width="200px"`, but just `width="200"`.
* **\[HTML `<img>` attribute\] loading** - This img attribute is used to tell the browser whether the image's loading should be delayed until it's near the viewport. Its default value is `loading="eager"`. In order to delay the image's loading until the user has scrolled far down enough, `loading="lazy"` should be used. One should not use lazy for images above the fold, only for those that are below the fold, since the user has to scroll down to reach them. For lazy images, if the user doesn't get to them, they'll never load, so that way bandwidth is not wasted. This wasn't necessary for this challenge in particular, but it's good to know anyway.
* **\[HTML `<img>` attribute\] fetchpriority** - If a image is very important and therefore should be prioritized, one can use `fetchpriority="high"`. It should only be used if the image is *really* important, since it will cause other stuff like scripts or fonts to be de-preoritized when the page is being loaded.
* **Tags `<picture>` and `<source>` (with the attributes 'srcset' and 'media')** - The `<picture>` tag always wraps a `<img>` tag and is used to provide alternative source images for a certain image. The alternative images can be of different size, format, pixel density, etc. For instance:
```html
<picture>
  <source srcset="small-image.png" media="(max-width: 500px)" width="300" height="300">
  <source srcset="medium-image.png" media="(max-width: 900px)" width="600" height="600">
  <img src="large-image.png" alt="Image's description" width="1000" height="1000" loading="lazy" />
</picture>
```
If the viewport width is narrower than 500px, the small image will be loaded. In case it's not, the browser will check the next source tag and see if the media condition is met. That is, if the viewport width is narrower than 900px but greater than 500px (otherwise the first image would be loaded right away), the medium image will be loaded. The source inside the `<img>` serves as a fallback in case none of the previous images in `<source srcset="...">` were loaded. This commands the browser to do more adequate choices and can save bandwidth, since the large image is heavier.
It's worth mentioning that the media condition is not mandatory. If the browser, for some reason, can't load that image (even if the optional media condition is met), it'll try to load the next one. For instance, if the image format the user's trying to load is not supported by that browser, then it won't load and the next source will be checked. 

#### The CSS stuff

* **`aspect-ratio: x/y`** - Used to render the image with an aspect-ratio that differs from the image's real dimensions. For instance, if we have `aspect-ration: 2/1`, then the image's width will be twice its height.
* **`object-fit: contain`** - tells the browser to preserve the image's aspect ratio, even if that means leaving empty space above and below. Generally speaking, the `object-fit` property specifies how the replaced element's content object should be fitted to the containing element's box. Some of the values it can take are: 'fill', 'contain', 'cover', 'scale-down' or 'none'.
* **`object-fit: cover`** - tells the browser to preserve the image's aspect ratio, even if that means cropping the image at the top and bottom.
* **`object-position: ...`** - If `object-fit: cover` crops the image in a problematic way, this property can be used to change the focus of the crop. It can take keywords like 'top', 'bottom', 'right top', 'top center', or percentage/length values, or even edge offsets values.
Generally speaking, this property controls the alignment of the replaced element inside it's container.

### Continued development

* Write cleaner and concise CSS code.
* Study more about the CSS attributes for replaced elements (like object-fit and object-position).
* Improve my intuition for building responsive layouts.
* Learn more about the different length units use cases.

### Useful resources

- [Responsive Images by web.dev](https://web.dev/learn/design/responsive-images) - Covers the aforementioned HTML attributes for images and more.
- [Picture Element by web.dev](https://web.dev/learn/design/picture-element) - More about the `<picture>` element and its use cases.
- [object-position by MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/object-position) - Extensive reference about the object-position property and its accepted values.
- [object-fit by MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit) - Extensive reference about the object-fit property and its accepted values.
- [Replaced Elements by MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element) - Article about replaced elements and how CSS handles them. I find these to be very tricky and this brief resource has deepened my understanding about them.

## Author

- Frontend Mentor profile - [@Oczywsziysya](https://www.frontendmentor.io/profile/Oczywsziysya)