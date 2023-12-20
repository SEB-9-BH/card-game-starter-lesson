# ![CSS Card Deck - Overview and Pseudocode](./assets/hero.png)

## Overview

The purpose of this lesson is to provide basic instructions for using the [CSS Card Deck](https://github.com/SEI-Remote/css-card-deck). This repository contains a style sheet and set of images that allow HTML elements to be styled as playing cards by adding/removing class names. 

## Pseudocode Roadmap

[tktk for QA1, leave in long form or just have them paste shortform below?] 

<!-- 1. Declare variables (arrays) for two decks of cards.
2. Create HTML elements (two `<div>`s) for the card decks:
    1. Deck 1 should display the back of a card with a shadow outline, indicating a larger stack.
    2. Deck 2 should display an empty card outline.
3. Create cached element references for each of the card decks.
4. Add an event listener for the "Flip" button.
5. Write an initialization function that assigns 52 'cards' to deck 1.
6. Declare a `render()` function to display a card after it is 'flipped'.
7. Stub up a `handleClick()` function for the event listener to call.
    1. Select a random card from deck 1.
    2. Remove the card from deck 1.
    3. Add the card to deck 2.
    4. Call the `render()` function and pass the card to it.
8. Within the `render()` function:
    1. After the first card is picked, remove the outline on deck 2.
    2. Add the class name to display the card picked on deck 2.
    3. When half of the cards are flipped, move the shadow from deck 1 to deck 2.
    4. When the final card is picked, add an outline to deck 1. -->

Paste the following into the `**app.js**` file so that we have some nice commented pseudocode code to work with as we progress:

```javascript
// Declare deck variables

// Cached element references

// Functions

// Initialize deck 1 with array of 52 cards 

// Function to render deck state
  // Remove outline class when first card is picked
  // Removes previous picked card from deck 2 class list
  // Add current card picked to deck 2 element
  // Adjust shadow when deck gets above/below halfway full
  // Remove card back color and add outline when last card is picked

// Function to handle a button click:
  // Randomly select number from total cards remaining
  // Assign card with the random index to a variable
  // Add card picked to deck 2
  // Pass card picked to render function to display

// Event listeners

```

