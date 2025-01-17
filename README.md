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
      - [Applying HTML Semantics](#applying-html-semantics)
        - [🔷 `article` Element as Card Wrapper](#-article-element-as-card-wrapper)
        - [🔷 Wrap date with `time` Element](#-wrap-date-with-time-element)
      - [Setup Local Fonts](#setup-local-fonts)
      - [Implementing Responsiveness](#implementing-responsiveness)
      - [Make HTML Result Close to The Design](#make-html-result-close-to-the-design)
        - [🔷 Figma Strokes vs CSS Borders](#-figma-strokes-vs-css-borders)
        - [🔷 Line Height Issue](#-line-height-issue)
        - [🔷 Browser's Inspector Shows Dimensions With Decimal Numbers](#-browsers-inspector-shows-dimensions-with-decimal-numbers)
    - [Continued development](#continued-development)
    - [Useful resources](#useful-resources)
  - [Author](#author)
  - [Acknowledgments](#acknowledgments)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

### Screenshot

<img src="./_docs/screenshot.jpg" alt="screenshot" width="400"/>

### Links

- Solution URL: [https://www.frontendmentor.io/solutions/i-discovered-a-lot-of-things-on-this-blog-preview-card-challenge-pSdptSJhP1](https://www.frontendmentor.io/solutions/i-discovered-a-lot-of-things-on-this-blog-preview-card-challenge-pSdptSJhP1)
- Live Site URL: [https://finkusuma-dev.github.io/frontendmenter-blog-preview-card](https://finkusuma-dev.github.io/frontendmenter-blog-preview-card)

## My process

### Built with

- Semantic HTML5 markup
- Flexbox
- Mobile-first workflow

### What I learned

#### Applying HTML Semantics

##### 🔷 `article` Element as Card Wrapper

I coded the card to use the `article` tag to add semantic. But after reading Grace Snow's blog [^1] which also uses another "Card" challenge as a case, I changed the `article` to use only `div`. The blog explained that the Card Component will be used many times on a page, and having too much extra semantic will create more noise and not necessary. I wonder if too much semantic is actually annoying for the screen reader users.

##### 🔷 Wrap date with `time` Element

I found that the `time` element can be used to wrap date and time. It makes the datetime info readable by the search engine, thus giving a better search results. [^2]

#### Setup Local Fonts

I learned how to setup local variable font with this code:

```css
@font-face {
  font-family: 'Figtree';
  font-weight: 500, 800;
  src: url('./assets/fonts/Figtree-VariableFont_wght.ttf') format('truetype');
}
```

And setup local static fonts with this code:

```css
@font-face {
  font-family: 'Figtree';
  font-weight: 500;
  src: url('./assets/fonts/static/Figtree-Medium.ttf') format('truetype');
}
@font-face {
  font-family: 'Figtree';
  font-weight: 800;
  src: url('./assets/fonts/static/Figtree-ExtraBold.ttf') format('truetype');
}
```

> [!Note]
>
> The challenge is currently has the wrong static font asset for `500` weight. Instead of using `Figtree-SemiBold.ttf` use `Figtree-Medium.ttf`.If you use `Figtree-SemiBold.ttf`, it will make the `500` weight text to appear thicker. You can download the `Figtree-Medium.ttf` directly from the Google Fonts.
>
> I already posted the issue on discord and still waiting for the developers to fix it.
>
> This is the comparison if you're using `Figtree-SemiBold.ttf` as `500` weight. The variable font on the left, and static fonts on the right:
>
> <img src="./_docs/compare_fonts.jpg" width="500"/>

#### Implementing Responsiveness

To apply responsive styles, I utilized bootstrap v5 breakpoints [^3]. Using **sm** breakpoint value (576px) as separator between mobile and desktop designs.

```css
@media (min-width: 576px) {
}
```

Also I added padding so there are spaces on the left and right sides. It looks neat on very small screen size (320px).

<img src="./_docs/padding.jpg" width="200">

#### Make HTML Result Close to The Design

##### 🔷 Figma Strokes vs CSS Borders

I noticed that strokes in Figma and borders in CSS behave differently. If we look at blog card properties in Figma design, the blog card has stroke **inside** with the padding of `24px`.

I tried different values on the CSS padding and also tried CSS border and outline. And these are the pixel to pixel comparison between figma stroke and CSS border (with box-sizing: border-box) and CSS outline.

1. ```css
   border: 0.1rem solid var(--color-gray-950);
   padding: 2.4rem;
   ```

    <img src="./_docs/border_pad24.jpg" width="200"/>

2. ```css
   border: 0.1rem solid var(--color-gray-950);
   padding: 2.3rem;
   ```

    <img src="./_docs/border_pad23.jpg" width="200"/>

3. ```css
   outline: 0.1rem solid var(--color-gray-950);
   padding: 2.3rem;
   ```

    <img src="./_docs/outline_pad23.jpg" width="200"/>

4. ```css
   outline: 0.1rem solid var(--color-gray-950);
   padding: 2.4rem;
   ```

    <img src="./_docs/outline_pad24.jpg" width="200"/>

As you may notice, the result of #1 (using `border` and `24px` padding) looks the same with #4 (using `outline` and `24px` padding). But they're different:

The **borders** are drawn inside the element's box, so the overall card size includes the borders.

<img src="./_docs/box_border.jpg" width="400">

While the **outlines** are drawn outside the element's box, so the overall card size does not include the **outlines**. We can see in the inspector, the dimension of the box without the outlines. We can choose this option if in Figma the stroke property position is **outside**.

<img src="./_docs/box_outline.jpg" width="400">

So, I choose to use `border` and reduce the `padding` to `23px` to make the overall card size matches with the design. If I use `24px` for padding (Like it's on Figma design), it would make the card bigger for 2 pixels on horizontal and on vertical.

##### 🔷 Line Height Issue

I had issue with the size of text boxes. Despite I set the correct font-family, font-weight, font-size, and line-height, the size of boxes that contain the text are not the same with Figma. After trials and looking at MDN doc [^4], I found out that it is better not to use line-height value with the percent as unit.

The reason is, if we use the percent as unit and set the `line-height` somewhere up (in the body), the value that is passed down to the children is not the percent value itself, but the calculated value. So the children that have different font size, their line height seems off because they're using the parent's line-height.

```css
body {
  font-size: 16px;
  line-height: 150%;
}

h2 {
  font-size: 24px;
}
```

<img src="./_docs/lineHeight150%25.jpg" width="400"/>

(Note: The correct line height: 150% of 24px = 36px)

If you want to use dynamic value on the line height correctly, use it without percent. So `1.5` instead of `150%`.

```css
body {
  font-size: 16px;
  line-height: 1.5;
}

h2 {
  font-size: 24px;
}
```

Or you can set `150%` on the children elements. Both of these approaches work, but the weakness is you need to set it on all affected children.

```css
body {
  font-size: 16px;
  line-height: 150%;
}

h2 {
  font-size: 24px;
  line-height: 150%;
}
```

<img src="./_docs/lineHeight1.5.jpg" width="400"/>

##### 🔷 Browser's Inspector Shows Dimensions With Decimal Numbers

I noticed a strange thing: When inspecting the elements on the inspector tab, Some element dimensions have decimal numbers. And I discovered that it is related with the Operating System's Display Scale.

If we change the OS Display Scale, for example `125%`, the element's box dimensions can appear to have decimal numbers. But it only affects elements that we don't explicitly set the size.

For example, I set the blog card's width to `384px`, and I didn't specify the height, and I use `125%` display scale. On the inspector tab, the width was exactly `384px`, but the height was `521.6px`. To make the height shows round numbers, I set the page zoom level to `80%`, then it showed exactly `522px`.

If we do the calculations it kind of makes sense. `100px` in `125%` display scale is actually scaled up to `125px`. If we scale down `125px` to `80%`, it goes back to the normal value of `100px`. While actually, I don't have any clue why it shows decimal numbers in the first place. At least I can feel relieve when the browser showing the exact numbers like in the design.

<img src="./_docs/box_with_zoom100.jpg" width="400"/>
<img src="./_docs/box_with_zoom80.jpg" width="400"/>

(Note: Only tested it in on Linux, haven't tested it on other OS.)

### Continued development

- Usually when I saw a card component, it didn't have interactive elements inside the card. But the card element itself as a whole is interactive (can get focus, hover, has animation, etc). So this challange is a bit confusing to me. But nevertheless, I did the challenge by adding the anchor element inside the heading, wrapping the text.
- I used `figure` element to wrap the image, but I removed it. As this is only a component, and the blog page will list many of this components so the image won't relate with the main content of the page. What is you opinion?
- Is wrapping published date with the `time` element a best practice?
- I'm using BEM together with nested CSS. Do you recommend this method for more complex challenge?
- Feels free to give suggestions if you see some of my code needs improvements.
- And also I would greatly appreciate if you could review and give feedback (or comments) to my process and discoveries on this challenge.

### Useful resources

- [@font-face](https://devdocs.io/css/@font-face) & [selecting normal and bold fonts](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-weight#selecting_normal_and_bold_fonts) - How to setup local fonts.
- https://html5doctor.com/avoiding-common-html5-mistakes/#figure - Why we should avoid using `figure` elements at all time.
- https://www.joshwcomeau.com/css/pixel-perfection/ - This blog gives me general ideas of how to make the html result looks closely similar to the design.

(Some other resources are listed in the footnote of this README.)

<!-- - [Example resource 1](https://www.example.com) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Example resource 2](https://www.example.com) - This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept. -->

<!-- **Note: Delete this note and replace the list above with resources that helped you during the challenge. These could come in handy for anyone viewing your solution or for yourself when you look back on this project in the future.** -->

## Author

- Website - [Arifin Kusuma](https://github.com/finkusuma-dev)
- Frontend Mentor - [@finkusuma-dev](https://www.frontendmentor.io/profile/finkusuma-dev)
- Twitter - [@finkusuma_dev](https://www.twitter.com/finkusuma_dev)

## Acknowledgments

Thanks to discord member @Darkstar, who helped me discovering the static font issue in the challenge.

<!--
This is where you can give a hat tip to anyone who helped you out on this project. Perhaps you worked in a team or got some inspiration from someone else's solution. This is the perfect place to give them some credit.

**Note: Delete this note and edit this section's content as necessary. If you completed this challenge by yourself, feel free to delete this section entirely.** -->

[^1]: https://fedmentor.dev/posts/html-plan-product-preview/. Grace Snow's blog, giving example of how to translate a design into HTML.
[^2]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time. MDN HTML `time` element documentation.
[^3]: https://getbootstrap.com/docs/5.0/layout/breakpoints/. Bootstrap v5.0 breakpoints.
[^4]: https://developer.mozilla.org/en-US/docs/Web/CSS/line-height#prefer_unitless_numbers_for_line-height_values. MDN CSS `line-height` property documentation
