# Frontend Mentor - Recipe page solution

This is a solution to the [Recipe page challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/recipe-page-KiTsR8QQKm). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

-  [Overview](#overview)
   -  [The challenge](#the-challenge)
   -  [Screenshot](#screenshot)
   -  [Links](#links)
-  [My process](#my-process)
   -  [Built with](#built-with)
   -  [What I learned](#what-i-learned)
   -  [Useful resources](#useful-resources)
-  [Author](#author)
-  [Acknowledgments](#acknowledgments)

**Note: Delete this note and update the table of contents based on what sections you keep.**

## Overview

### Screenshot

![Desktop Design](<screenshot/Desktop Design - Recipe Page - AJ.png>)
![Mobile Design](<screenshot/Mobile Design - Recipe Page - AJ.png>)

### Links

-  Solution URL: [https://github.com/AJ-Tan/4.-Frontend-Mentor---Recipe-Page.git]
-  Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## My process

### Built with

-  Semantic HTML5 markup
-  CSS custom properties
-  CSS Grid

### What I learned

1. Custom Markers for Ordered/Unordered List.

```css
/*** Custom Marker ***/
:is(ul, ol) li {
   position: relative;
   counter-increment: item; /** For Ordered List Marker **/
}

ol li::before {
   content: counter(item) ".";

   position: absolute;
   left: calc(2em * -1);
   top: 0;

   font-weight: 600;
   font-size: 1eem;
}

ul li::before {
   content: "•";

   position: absolute;
   left: calc(2em * -1);
   top: 50%;

   font-size: 1em;

   transform: translateY(-50%);
}
```

2. How to write CSS in a clean, organized, and easily maintainable manner. (See Useful Resources)

### Useful resources

1. Custom Marker - I found that its really hard to make adjustments(margin/gap and etc) to the built in marker for ordered/unordered list. So I used this reference to make custom marker.

-  [Using ::before for the marker](https://stackoverflow.com/questions/40915850/css-ordered-list-styling-before-margins)
-  [Explained use of counter/counters for marker](https://www.smashingmagazine.com/2019/07/css-lists-markers-counters/)

![Ordered List Preview](<screenshot/ordered list - counter.png>)

```html
<ol>
   <li>Item 1</li>
   <li>Item 2</li>
   <li>
      Item 3
      <ol>
         <li>Sub Item 1</li>
         <li>Sub Item 2</li>
         <li>Sub Item 3</li>
      </ol>
   </li>
   <li>Item 4</li>
   <li>
      Item 5
      <ol>
         <li>Sub Item 1</li>
         <li>
            Sub Item 2
            <ol>
               <li>Super Sub Item 1</li>
               <li>Super Sub Item 2</li>
            </ol>
         </li>
      </ol>
   </li>
</ol>
```

```css
ol {
   list-style-type: none;
}

li {
   counter-increment: item;

   /* counter vs counters */
   /* counter: When there is no nested list.
    counters: When there is or the posibility of having nested list */
   &::before {
      /* Used counters so it will display the number sequence of each subsequent list delimited by "." which can be modified. */
      content: counters(item, ".") ":";
   }

   /* Reset counter per instance of ordered list up to 3rd level */
   /* So that each ordered list will have their respective sequence */
   ol {
      counter-reset: item;

      ol {
         counter-reset: item;
      }
   }
}
```

2. Clean, Organized, and Maintainable CSS.

-  [Social Links Solution - Comment Section](https://www.frontendmentor.io/solutions/frontend-mentor---social-links-profile-liVLORNdBY) -
-  [@mustafasen97](https://www.frontendmentor.io/profile/mustafasen97)

Use a consistent order for CSS properties

A common and popular convention is:

1. Positioning (position, top, right, bottom, left, z-index)
2. Display & Flex/Grid (display, flex properties, grid properties)
3. Box Model (width, height, padding, margin, border, box-sizing)
4. Typography (font-size, font-weight, color, text-align, line-height)
5. Background & Decoration (background, border-radius, box-shadow, etc.)
6. Other (cursor, transition, animation, etc.)

Example (reordered):

```css
.profile-card {
   container-type: inline-size;
   display: grid;
   justify-self: center;
   gap: var(--spacing-md);

   width: clamp(15rem, 100%, 19rem);
   padding: var(--spacing-lg);
   border-radius: 1rem;

   background-color: var(--grey-800);
}
```

Group similar parts together

Separate your base / reset, variables, layout, components, and utilities:

```css
/**** Base styles ****/
* {
   ...;
}
html,
body {
   ...;
}
body,
a {
   ...;
}

/**** Variables ****/
:root {
   ...;
}

/**** Layout ****/
main {
   ...;
}

/**** Components ****/
.profile-card {
   ...;
}
.profile-card__header {
   ...;
}
.profile-card__image {
   ...;
}
.profile-card__user-details {
   ...;
}
.profile-card__social-media {
   ...;
}

/**** Utilities or helpers ****/
/* if you have */
```

Add comments

Clear section comments help quickly scan large CSS files.

```css
/**** PROFILE CARD HEADER ****/
.profile-card__header {
   ...;
}

/**** SOCIAL MEDIA LIST ****/
.social-media__list {
   ...;
}
```

Keep nesting shallow

Nesting too deep (like .profile-card .profile-card**header .profile-card**user-details) can make CSS harder to maintain. One or two levels is usually enough.

Use shorthand where practical

For example:

```css
padding: var(
   --spacing-lg
); /* instead of padding-block, padding-inline separately */
border-radius: 0.5rem; /* instead of writing all corners separately */
```

In summary:

1. Pick and stick to a property order (position → layout → box → typography → visuals → other)
2. Group by component
3. Use comments for sections
4. Keep selectors flat & short
5. Use tools to auto-format

## Author

-  GitHub - [AJ-Tan](https://github.com/AJ-Tan)
-  Frontend Mentor - [@AJ-Tan](https://www.frontendmentor.io/profile/AJ-Tan)

## Acknowledgments

Frontend Mentor:
[@mustafasen97](https://www.frontendmentor.io/profile/mustafasen97) - I would like to thank Mr. Mustafa for giving me constructive guidance on how I can manage and organize my CSS in a solution I submitted in Frontend Mentor (Social Links Profile). I applied his suggestion, and I can see that my CSS looks a lot more cleaner, organized and easy to maintain. Though I probably didn't properly applied everything, but I will make continuous improvement down the line. Thank you!
