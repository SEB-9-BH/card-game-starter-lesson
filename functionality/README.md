# ![Card Game Starter - Functionality](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to use JavaScript to create the flipping card functionality for our card deck.

Let's start with the HTML. We'll need two `<div>`s for our deck (`deck-1` and `deck-2`) and a 'Flip Card' button. Add the following inside the HTML body: 

```html
<div class="container">
  <div id="deck-2" class="card large outline"></div>
  <div id="deck-1" class="card large back-blue shadow"></div>
</div>
<button id="btn" class="btn">Flip Card</button>
```

With the HTML adjustments out of the way, let's go set up a few variables in `app.js`:

```javascript
// Declare variables
let deck1 = []
let deck2 = []
let cardToRemove

// Cached element references
let deck1El = document.querySelector('#deck-1')
let deck2El = document.querySelector('#deck-2')
```

Next, stub up the event listener and test it out in the browser with a `console.log()`:

```javascript
// Event listeners
document.querySelector('#btn').addEventListener('click', ()=> console.log('clicked'))
```

Next, let's create and invoke an initialization function. The purpose of this function is to put a fresh set of 52 cards into `deck1`. 

> This step isn't technically necessary, as we could just add the cards when we declare the decks. This code allows for the addition of a reset feature, which you should challenge yourself to implement after the lecture.

```javascript
// Functions
// Initialize deck 1 with array of 52 cards
const init = () => {
  deck1 = ["dA","dQ","dK","dJ","d10","d09","d08","d07","d06","d05","d04","d03","d02","hA","hQ","hK","hJ","h10","h09","h08","h07","h06","h05","h04","h03","h02","cA","cQ","cK","cJ","c10","c09","c08","c07","c06","c05","c04","c03","c02","sA","sQ","sK","sJ","s10","s09","s08","s07","s06","s05","s04","s03","s02"]
}
// invoke the function
init()
```

> 🧠 Note that the strings we're using to represent each card in the deck match one-to-one with the selector names in `cardStarter.css`. This is how we'll be able to dynamically style the card, based on whichever random element is picked from our deck.

Next, let's write a function to handle a button click. Add the pseudocode from our list into the function so we have easy access to our list of things to do:

```javascript
// Function to handle a button click:
const handleClick = () => {
  // Randomly select number from total cards remaining
  // Assign card with the random index to a variable
  // Add card picked to deck 2
  // Pass card picked to render function to display
}
```

Then, let's update our event handler to call this function instead of `console.log()`:

```javascript
document.querySelector('#btn').addEventListener('click', handleClick)
```

The other function we'll need is `render()`. As we did with `handleClick()`, add our pseudocode to the function body: 

```javascript
const render = () => {
	// Remove outline class when first card is picked
  // Removes previously picked card from deck 2 class list
  // Add current card picked to deck 2 element
	// Adjust shadow when deck gets above/below halfway full
	// Remove card back color and add outline when last card is picked
}
```

> `handleClick()` will invoke `render()`, so make sure you initialize the render function above the click handler.

Let's start fleshing out our functions by turning our pseudocode into actual code. We'll start with `handleClick()`:

```javascript
const handleClick = () => {
  // Used to prevent error on click when no cards are left in deck 1
  if (deck1.length > 0) {  

    // Randomly select number from total cards remaining
    let randomIdx = Math.floor(Math.random() * deck1.length)

    // We use splice and the random index to remove a random card 
    // from the deck. Then, we assign that card to a variable. 
    let cardPicked = deck1.splice(randomIdx, 1)[0]

    // Add the picked card to deck 2
    deck2.push(cardPicked) 

    // Pass the picked card to the render function to display
    render(cardPicked)
  }
}
```

Notice that we're passing our `cardPicked` variable to `render()` as an argument. We'll need to add a `cardPicked` parameter to our render function in order to access this variable within it, so let's do that next: 

```javascript
function render(cardPicked){
  // Remove outline class when first card is picked
  // Removes previously picked card from deck 2 class list
  // Add current card picked to deck 2 element
  // Adjust shadow when deck gets above/below halfway full
  // Remove card back color and add outline when last card is picked
}
```

The final piece of the puzzle is the body of the `render()` function, which will use the `cardPicked` parameter we just added to update the state of our application. Notice how we're the `cardToRemove` variable (we created it as a global variable way back at the start) to store the card that will need to be removed the NEXT time `render()` is called.

```javascript
const render = (cardPicked) => {

  // Removes outline class when first card is picked
  if (deck2.length === 1) {  
    deck2El.classList.remove("outline")
  }

  // Remove previous picked card from deck2's class list. 
  if (deck2.length > 1) {  
    deck2El.classList.remove(cardToRemove)
  }

  // Set card to be removed on next click
  cardToRemove = cardPicked  

  // Apply current picked card deck2's class list. For example, if picked card was "h08", the the deck2El would gain the class "h08", which correlates to a background image of the eight of hearts. 
  deck2El.classList.add(cardPicked)  

  // Check which deck has the majority of cards. Once deck2 has more cards, remove shadow from deck1 and apply it to deck2.
  if (deck2.length === 26) {  
    deck2El.classList.add("shadow");
    deck1El.classList.remove("shadow");
  }
	
  // If the deck is empty, add an outline and remove the card back color
  if (deck1.length === 0) {  
    deck1El.classList.add("outline");
    deck1El.classList.remove("back-blue");
  }
}
```

Congrats! Your flipping cards are ready for your game! 