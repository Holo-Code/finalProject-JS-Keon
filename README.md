# finalProject-JS-Keon
# Assignment 3

## Purpose

This vanilla JavaScript web app displays various daily menus which can be viewed by clicking either the next or previous buttons.  

![Image of app](app.JPG)

## Concepts Learned

To create this "Bun on the Run" menu app the following JavaScript concepts were used:
- variables let vs const
- Arrays
- Functions
- Loops
- Objects/Embedded Objects
- EventListeners
- QuerySelectors
- TextContent vs InnerHTML

## How I made the web app

1. First I defined a const called menus and assigned it to be an empty array
    ```js
    const menus = []
    ```
    The reason why I did that is because the menus array will eventually be assigned an array of objects where each object represents a daily menu, complete with menu items and prices.

1. Next I defined a let variable for the page index/number
    ```js
    let currentIndex = 0;
    ```
    The reason why I did that is because we need to be able to navigate through the different menus and setting a variable that allows us to dynamically change the value.
    

1. Next I defined a const that will hold the querySelector to scoop up the HTML
    ```js
    const menuTitle = document.querySelector("#menu h2");
    ```
    The reason why I did that is because we need to be able to change the HTML for the user to see.

1. Next I defined a function called display that accepts a value called todaysmenu
    ```js
    function display(todaysmenu) {
        menuTitle.textContent = todaysmenu.title;
        soup.title.textContent = todaysmenu.soup;
        soup.price.textContent = todaysmenu.soupPrice;
        ...etc...
    }
    ```
    This function displays the current menu.  For exammple, it displays the menu title by first using the querySelected element and replace the textContent to what the new menus title would be.

1. Next I defined a function called getJson which will fetch our menus data in JSON format
    ```js
    async function init() {
        const res = await fetch("____________________________");
        const data = await res.json();
        menu.push(...data);
        display(menu[currentIndex]);
    }
    ```
    First I defined a constant called res which will be assigned the URL for the RAW version of JSON.
    
    Next I defined a const called data which is assigned the await JSON line to allow us to fetch it.

    Next I inserted that entire array of objects into our menus array by .push with the (...data)

    Next I called the function display to display our current menu passing in the argument of our first menu in our array

1.  Next I defined a function called prev which takes no parameter but decrements our currentIndex by 1 then calls our display function
    ```js
    function prev() {
        currentIndex = currentIndex === 0 ? menu.length - 1 : currentIndex - 1;
        display(menu[currentIndex]);
    }
    ```
    The reason I'm manipulating the value of currentIndex is so we can dynamically go through the different menu numbers.

1.  In similar fashion, I also created a function called next with similar logic.
    ```js
    function next() {
        currentIndex = currentIndex === menu.length - 1 ? 0 : currentIndex + 1;
        display(menu[currentIndex]);
    }
    ```

1.  Next I added some click event listeners to both next and previous buttons
    ```js
    previousMenu.addEventListener("click", prev);
    nextMenu.addEventListener("click", next);
    ```
    The reason for adding click event handlers is so that when users press either the left or right arrow either the next or previous functions will run which will allow the navigation through the menus.

1.  Finally, I initalise the page with the intit(); function.
    ```js
    init();
    ```

# Reflection
## What is the hardest part of creating this web app?
- Selecting the right ids from the HTML and making sure that I'm testing to make sure that the correct ones are selected and working.

## What remaining JS concepts are still kind of foggy?
- Fetching JSON data could be worked on, I partially understand the concept of it and I'm currently looking over it to further understand the meaning behind each line.

## Deck of cards API (remnant of Assignment 4)
Given the documentation listed here: https://deckofcardsapi.com/ it lists 2 APIs/REST endpoints `Shuffle the Cards` and `Draw a card`.  What would you need to do to draw 1 card?
- Replace the deck ID to be able to use it as an identifier.
