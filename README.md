# Frontend Mentor - Blog preview card solution

This is a solution to the [Blog preview card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/blog-preview-card-ckPaj01IcS). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Frontend Mentor - Blog preview card solution](#frontend-mentor---blog-preview-card-solution)
  - [Table of contents](#table-of-contents)
  - [Overview](#overview)
    - [The challenge](#the-challenge)
    - [Screenshot](#screenshot)
    - [Links](#links)
  - [My process](#my-process)
    - [Built with](#built-with)
    - [What I learned](#what-i-learned)
      - [Interactive Elements](#interactive-elements)
      - [Applying HTML Semantics](#applying-html-semantics)
        - [`<article>` as Card Component](#article-as-card-component)
        - [Wrap date with `<time>`](#wrap-date-with-time)
      - [Setup Local Font](#setup-local-font)
      - [Implementing Responsiveness](#implementing-responsiveness)
      - [Building Close to The Design](#building-close-to-the-design)
    - [Continued development](#continued-development)
    - [Useful resources](#useful-resources)
      - [HTML Semantic](#html-semantic)
      - [Setup Local Font](#setup-local-font-1)
      - [Implementing Responsiveness](#implementing-responsiveness-1)
      - [Building Close to The Design](#building-close-to-the-design-1)
  - [Author](#author)
  - [Acknowledgments](#acknowledgments)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

### Screenshot

<img src="./_docs/screenshot.jpg" alt="screenshot" width="400"/>

### Links

- Solution URL: [Add solution URL here](https://github.com/finkusuma-dev/frontendmenter-blog-preview-card)
- Live Site URL: [Add live site URL here](https://finkusuma-dev.github.io/frontendmenter-blog-preview-card)

## My process

### Built with

- Semantic HTML5 markup
- Flexbox
- Mobile-first workflow

### What I learned

#### Interactive Elements

To make **header** element interactive I added anchor to the text element, so the **header** structure inside is: Header > Anchor > Text. While the other 2 elements (**category** and **author**) I used the `anchor` element and gave it a class.

#### Applying HTML Semantics

##### `<article>` as Card Component

At first, I coded the card to use the `article` tag as it adds the semantic. But after reading Grace Show's blog, "How to translate a design into HTML" which also uses another "Card" challenge as a case, I changed the `article` to use only `div`. The blog explained that the Card Component will be used many times on a page, and having too much extra semantic will create more noise and it's not necessary. I wonder if too much semantic is actually annoying for the screen reader users.

##### Wrap date with `<time>`

I found that the `time` tag can be used to wrap date and time. It makes the datetime info readable by the search engine, thus giving a better search results.

#### Setup Local Font

I learnt how to setup font locally.

- There is problem with the static fonts, maybe I have wrong setup. But I must check it, maybe by trying to extract the font weights from the variable font myself.

#### Implementing Responsiveness

To apply responsive style, I utilized bootstrap v5 breakpoints. Using sm breakpoint value (576px) as separator between mobile and desktop designs.

```css
@media (min-width: 576px) {
}
```

Also I added `padding`, so there are spaces on the left and right sides. Look neat when the page is viewed on very small device.

#### Building Close to The Design

- Figma inline border has different behavior than the html style.
- Putting line-height on the body made the elements to have different height than the design. So I must set it on each of the text.
  After looking at the MDN documentation it's mentioned it's preferred to have line-height without unit. If the line height has a unit (like px, rem, rem, or %), the line height is calculated on the parent then the result passed down to the children. If line-height doesn't have a unit (i.e: 1.5), the value is directly passed down to the children and then calculated there against the children font size.
- The element dimensions that is shown when we hover on Inspector tab is affected by the Operating System Display Scale. For example, on the design the element's width is 200px. On OS that has display scale 125%, using inspector we will see it's width is not exactly 200px but 200px. To make thing normal scale the page to 80%.

### Continued development

Use this section to outline areas that you want to continue focusing on in future projects. These could be concepts you're still not completely comfortable with or techniques you found useful that you want to refine and perfect.

**Note: Delete this note and the content within this section and replace with your own plans for continued development.**

### Useful resources

#### HTML Semantic

- https://fedmentor.dev/posts/html-plan-product-preview/
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time

#### Setup Local Font

- [@font-face](https://devdocs.io/css/@font-face) & [selecting normal and bold fonts](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-weight#selecting_normal_and_bold_fonts)

#### Implementing Responsiveness

- https://getbootstrap.com/docs/5.0/layout/breakpoints/

#### Building Close to The Design

- https://www.joshwcomeau.com/css/pixel-perfection/
- https://developer.mozilla.org/en-US/docs/Web/CSS/line-height#prefer_unitless_numbers_for_line-height_values.

<!-- - [Example resource 1](https://www.example.com) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Example resource 2](https://www.example.com) - This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept. -->

<!-- **Note: Delete this note and replace the list above with resources that helped you during the challenge. These could come in handy for anyone viewing your solution or for yourself when you look back on this project in the future.** -->

## Author

- Website - [Arifin Kusuma](https://github.com/finkusuma-dev)
- Frontend Mentor - [@finkusuma-dev](https://www.frontendmentor.io/profile/finkusuma-dev)
- Twitter - [@finkusuma_dev](https://www.twitter.com/finkusuma_dev)

**Note: Delete this note and add/remove/edit lines above based on what links you'd like to share.**

## Acknowledgments

This is where you can give a hat tip to anyone who helped you out on this project. Perhaps you worked in a team or got some inspiration from someone else's solution. This is the perfect place to give them some credit.

**Note: Delete this note and edit this section's content as necessary. If you completed this challenge by yourself, feel free to delete this section entirely.**
