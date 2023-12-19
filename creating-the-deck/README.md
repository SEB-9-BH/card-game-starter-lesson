# ![CSS Card Deck - Creating The Deck](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

Let's start with the HTML.  We'll need two deck <div>s and a button.  (Note the Bootstrap CDN link in the <head> of our HTML.  Let's also fancy up that button.  NOBODY likes plain buttons.)

```html
<body>
	<div class="container">
		<div id="deck-2" class="card large outline"></div>
		<div id="deck-1" class="card large back-blue shadow"></div>
	</div>
	<button id="btn" class="btn">Flip Card</button>
</body>
```

Now that the HTML is out of the way, let's go set up a few variables in `app.js`:

```javascript
// Declare variables
let deck1 = []
let deck2 = []
let cardToRemove

// Cached element references
let deck1El = document.getElementById('deck-1')
let deck2El = document.getElementById('deck-2')
```

Next, stub up the event listener and test it out in the browser with a `console.log()`:

```javascript
// Event listeners
document.getElementById('btn').addEventListener('click', ()=> console.log('clicked'))
```

Stub up and invoke an initialization function.  The purpose of this function is to put a fresh set of 52 cards into deck 1.  (This step isn't technically necessary, as we could just add the cards when we declare the decks.  This code allows for the addition of a reset feature, which you should challenge yourself to implement after the lecture!):

```javascript
// Functions
init()

// Initialize deck 1 with array of 52 cards
function init() {
  deck1 = ["dA","dQ","dK","dJ","d10","d09","d08","d07","d06","d05","d04","d03","d02","hA","hQ","hK","hJ","h10","h09","h08","h07","h06","h05","h04","h03","h02","cA","cQ","cK","cJ","c10","c09","c08","c07","c06","c05","c04","c03","c02","sA","sQ","sK","sJ","s10","s09","s08","s07","s06","s05","s04","s03","s02"]
}
```

Next, let's write a function to handle a click on the button.  Pop the pseudocode from our list into the function so we have easy access to our list of things to do.  e can also update our event handler to call this function instead of `console.log()`:

```javascript
// Function to handle a button click:
function handleClick() {
    // Randomly select number from total cards remaining
    // Assign card with the random index to a variable
    // Add card picked to deck 2
    // Pass card picked to render function to display
}
```

The last function we'll need is render().  STUB IT UP!!!!:

```javascript
function render(cardPicked){
	 // Remove outline class when first card is picked
   // Removes previous picked card from deck 2 class list
   // Add current card picked to deck 2 element
	 // Adjust shadow when deck gets above/below halfway full
	 // Remove card back color and add outline when last card is picked
}
```

We've got some good bones, let's start fleshing out our functions by turning our pseudocode into actual code.  Let's start with handleClick():

```javascript
function handleClick() {

	// Used to prevent error on click when no cards are left in deck 1
  if (deck1.length > 0) {  

	  // Randomly select number from total cards remaining
		let randIdx = Math.floor(Math.random()*deck1.length)

		// Assigns card with the random index to a variable   
	  let cardPicked = deck1.splice(randIdx, 1)[0]

	  // Adds card picked to deck 2
		deck2.push(cardPicked) 

	  // Pass card picked to render function to display
		render(cardPicked)
  }
}
```

The final piece of the puzzle is the `render()` function, which will use `cardPicked` to update the state of our application.  Notice how we're using `cardToRemove` as a variable to store the card that will need to be removed the NEXT time `render()` is called.

```javascript
function render(cardPicked) {

  // Removes outline class when first card is picked
  if (deck2.length === 1) {  
    deck2El.classList.remove("outline")
  }

	// Remove previous picked card from deck 2 class list
  if (deck2.length > 1) {  
    deck2El.classList.remove(cardToRemove)
  }

	// Set card to be removed on next click
  cardToRemove = cardPicked  

	// Add current card picked to deck 2 array
  deck2El.classList.add(cardPicked)  

	// Adjust shadow when deck gets above/below halfway full
  if (deck2.length === 26) {  
    deck2El.classList.add("shadow");
    deck1El.classList.remove("shadow");
  }
	
	// Remove card back color and adds outline when last card is picked
  if (deck1.length === 0) {  
    deck1El.classList.add("outline");
    deck1El.classList.remove("back-blue");
  }
}
```

