# Manipulating the DOM

## Learning objectives

* Explain at a high-level what is the DOM (Document Object Model) and how we can use it with JS
* Query DOM elements with JS using document.querySelector
* Modify the page content
* Listen to user events and respond by changing the page

### DOM - Document Object Model

What is the DOM?
The Document Object Model (DOM) connects web pages to scripts or programming languages by representing the structure of a document—such as the HTML representing a web page—in memory. 

What are the DOM "tree" and elements (also called nodes)?
The DOM represents a document with a logical tree. Each branch of the tree ends in a node, and each node contains objects. 
Nodes can also have event handlers attached to them. Once an event is triggered, the event handlers get executed.

Why do we use it?
DOM methods allow programmatic access to the tree. With them, you can change the document's structure, style, or content.

### Exercise

I will now demonstrate how I worked through these exercises.
I was presented with the following code:

```
<!doctype html>
<html>
    <head>
        <title>My TODO list</title>
        <link href="style.css" media="screen" rel="stylesheet" />
    </head>
    <body>
      <h1>My TODO list</h1>

      <button id="add-item">Add Todo item</button>
      
      <div id="todo-list">
        <div class="todo-item">
          Reflect on my learning
        </div>
        <div class="todo-item">
          Cancel gym membership
        </div>
        <div class="todo-item">
          Donate clothes to charities
        </div>
      </div>

      <script src="bundle.js"></script>
    </body>
</html>
```

Within the JS document and/or developer console in Chrome, I completed the following prompts:

Change the second item's text to "Renew gym membership and go to the gym!"
```
const item = document.querySelector('#todo-list :nth-child(2)');
item.innerText = "Renew gym membership and go to the gym!"
```

Add a new todo item on the list (with the text of your choice!)
```  
const parent = document.querySelector('#todo-list');
const newItem = document.createElement('div');
newItem.className = 'todo-item';
newItem.innerText = "Sing";
parent.append(newItem);
```

Loop through all the todo item elements (hint: use the class selector for this) and change each item's text prefixing it by "TODO: ".
```
parent.forEach(item => {
item.innerText = "Todo: " + item.innerText})
```

Attach a listener on 'click' to the button, so a new todo item is added on the page
```
const myButton = document.querySelector('#add-item');
myButton.addEventListener('click', () => {
let myItem = document.createElement('div');
myItem.className = 'todo-item';
myItem.innerText = 'Anything eggs';
parent.append(myItem);
});
```

Add a new button in the HTML page called "Clear all" (you might duplicate the existing one - don't forget to change the id too)
```
const newButton = document.createElement('button');
newButton.setAttribute("id", "clear-all");
newButton.textContent = 'Clear All';
myButton.before(newButton);
```

Attach a listener on 'click' to that new button, so all todo items are removed from the page.
```
newButton.addEventListener('click', () => {
const items = document.querySelectorAll('.todo-list');
items.forEach(item => item.remove())
});
```

## Takeaway
This workshop has been very enlightening and helpful. I have a thorough understanding of the DOM and how to query it to dynamically modify the page content.

What I found challenging was having to find the correct syntax to access certain ids, classes or tags; and finding out which attributes each tag relates to. For example an input tag would have a value attribute whereas a div tag would not.