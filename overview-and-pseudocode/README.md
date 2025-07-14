<h1>
  <span class="headline">Card Game Starter</span>
  <span class="subhead">Overview and Pseudocode</span>
</h1>

**Learning objective:** By the end of this lesson, students will review the pseudocode for utilizing the Card Game Starter library to create and manipulate a deck of playing cards. 

## Overview

The purpose of this lesson is to provide basic instructions for using the Card Game Starter Code. This repository contains a style sheet and set of images that allow HTML elements to be styled as playing cards by adding and removing class names. 

## Pseudocode Roadmap

Paste the following into the **`app.js`** file so that we have some nice commented pseudocode code to work with as we progress:

```javascript
// 1. Declare variables (arrays) for two decks of cards.
// 2. Create HTML elements (two <div>s) for the card decks:
  // 1. Deck 1 should display the back of a card with a shadow outline, indicating a larger stack.
  // 2. Deck 2 should display an empty card outline.
// 3. Create cached element references for each of the card decks.
// 4. Add an event listener for the "Flip" button.
// 5. Write an initialization function that assigns 52 cards" to deck 1, then invoke it.
// 6. Declare a render() function to display a card after it is flipped.
// 7. Stub up a handleClick() function for the event listener to call.
  // 1. Select a random card from deck 1.
  // 2. Remove the card from deck 1.
  // 3. Add the card to deck 2.
  // 4. Call the render() function and pass the card to it.
// 8. Within the render() function (situated above handleClick()):
  // 1. After the first card is picked, remove the outline on deck 2.
  // 2. Add the class name to display the card picked on deck 2.
  // 3. When half of the cards are flipped, move the shadow from deck 1 to deck 2.
  // 4. When the final card is picked, add an outline to deck 1.
```
```js
// Declare variables
var deck1 = [];
var deck2 = [];

// Cached element references
var deck1El = document.getElementById('deck1');
var deck2El = document.getElementById('deck2');

// Event Listeners
document.getElementById('btn').addEventListener('click',handleClick)

// Functions
init();

// Initialize deck 1 with array of 52 cards using 
//  provided CSS class names
function init() {
    deck1 = ["dA","dQ","dK","dJ","d10","d09","d08","d07","d06","d05","d04","d03","d02","hA","hQ","hK","hJ","h10","h09","h08","h07","h06","h05","h04","h03","h02","cA","cQ","cK","cJ","c10","c09","c08","c07","c06","c05","c04","c03","c02","sA","sQ","sK","sJ","s10","s09","s08","s07","s06","s05","s04","s03","s02"]
}

// Function to handle a button click:
function handleClick() {

    if (deck1.length > 0) {  // Used to prevent error on click when no cards are left in deck 1
    let randIdx = Math.floor(Math.random()*deck1.length);   // Randomly selects number from total cards remaining
    cardPicked = deck1.splice(randIdx, 1) // Assigns card with the random index to a variable
    deck2.push(cardPicked);  // Adds card picked to deck 2
    render(cardPicked);  // Passes card picked to render function to display
    }
}

// Function to render new deck state
function render(cardPicked) {
    
    if (deck2.length === 1) {  // Removes outline class when first card is picked
        deck2El.classList.remove("outline");
    }

    if (deck2.length > 1) {  // Removes previous picked card from deck 2 class list
        deck2El.classList.remove(cardToRemove);
    }

    cardToRemove = cardPicked;  // Sets card to be removed on next click
    deck2El.classList.add(cardPicked);  // Adds current card picked to deck 2 array

    if (deck2.length === 26) {  // Adjusts shadow when deck gets above/below halfway full
        deck2El.classList.add("shadow");
        deck1El.classList.remove("shadow");
    }

    if (deck1.length === 0) {  // Removes card back color and adds outline when last card is picked
        deck1El.classList.add("outline");
        deck1El.classList.remove("back-red");
    }
}
```
