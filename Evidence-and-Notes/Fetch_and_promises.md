# Learning goals

* Send an HTTP request using fetch.
* Execute code to change the page when the response is received.
* Use await to make our code "wait" for the promise value.

## Fetch
Consider the following code:
```
const fetchPromise = fetch('https://mdn.github.io/learning-area/javascript/apis/fetching-data/can-store/products.json');

console.log(fetchPromise);

fetchPromise.then( response => {
  console.log(`Received response: ${response.status}`);
});

console.log("Started request...");
```
`Fetch` sends an HTTP request to the given URL, and returns a `fetchPromise` variable.
Logging the `fetchPromise` variable would initialize a promise and would appear as `Promise { <state>: "pending" }`
Note: Even though we are not creating the Promise value ourselves, it is created by fetch under the hood — and we use it to access the response when it becomes available. Promise won’t be available right away, but will 'fullfil' it later.
Calling .then (and if fetch operation succeeds), the promise will pass in a response object which contains the servers response.

### The process

Call fetch() 
Promise is iniatialised
HTTP request is sent
Promise state moves to pending
**IF HTTP response is received**
Promise state moves to ‘fulfilled'
The callback function given to .then() is called
**IF HTTP request fails**
Promise state moves to ‘rejected’

### Exercise
Consider the following code:
```
class View {
  loadPeople() {
    const something = fetch('https://async-workshops-api.herokuapp.com/people');

    console.log(something); // what is this?
  }
}

module.exports = View;
```
Use fetch to make a request to https://async-workshops-api.herokuapp.com/people, and when the response is received:

1. Display the received data into the console.
```
//view.js
loadPeople(callback) { //callback function to callback on line 6
  fetch('https://async-workshops-api.herokuapp.com/people')
    .then(response => response.json()) //take the raw response and convert to json which returns a promise
    .then(data => { //chains on a promise 
      callback(data) //called back to load the data
    });
};

//index.js
const View = require('./view');

const view = new View();
view.loadPeople((callback) => {
  console.log(callback)
})
```
2. Change the content of the page to add one new element for each name in the JSON list (append them to the \#container div). You'll know it works if you reload the page and see the list of names being displayed on the page.
```
//view.js
displayPeople(people){
  people.forEach(person => {
    const div = document.createElement('div');
    div.innerText = person.name;
    document.querySelector('#container').append(div)
  })

//index.js
const View = require('./view');

const view = new View();
view.loadPeople((callback) => {
  console.log(callback)
  view.displayPeople(callback)
})
```
3. Instead of fetching (and showing) the list of people straight when the page loads, make it happen when the user clicks on the button.
```
//view.js
  constructor() {
    this.button = document.querySelector('#button')
    };
  

  click(people) {
    this.button.addEventListener('click', () => {
      this.displayPeople(people);
    });
  }
  
//index.js
const View = require('./view');

const view = new View();
view.loadPeople((callback) => {
  console.log(callback)
  view.click(callback)
})
```
### Discussion

What type of HTTP request does fetch send?
Sends a GET request

How we can we handle failures?
Chaining a `.catch` to catch any errors if there are failures from the fetch requests. While the handler passed to `then()` is called when the asynchronous operation succeeds, the handler passed to `catch()` is called when the asynchronous operation fails. 

Why do we need to call .then twice?
This is chaining promises - one promise for the actual request grabs the raw data nd converts to a json response, and the second promise for to return the data extracted from the json response.

## Await
Consider the following code:
```
const promise = await fetch('https://async-workshops-api.herokuapp.com/people');

console.log(promise); // what is this?
```
Using await in front of fetch allows us to directly get the result — however, this means our code now "waits" for fetch to receive the response.

### Exercise
Update the exercise code to use await for the two promises, and remove the two calls to .then()
 ```
 loadPeople(callback) {
  const response = await fetch('https://async-workshops-api.herokuapp.com/people')
  const data = await response.json()
  callback(data)
};
```
Check the terminal where npm run build is running — it's likely you got the following error:
`"await" can only be used inside an "async" function`
Follow the error output suggestions to add the async keyword, and reload the page.
```
async loadPeople(callback) {
  const response = await fetch('https://async-workshops-api.herokuapp.com/people')
  const data = await response.json()
  callback(data)
};
```
### Discussion

What can you say about the behaviour of await and async?
The async and await keywords enable asynchronous, promise-based behavior to be written in a cleaner style, avoiding the need to explicitly configure promise chains.
The await keyword waits for things on the right hand side to process and stores it into a variable on the left hand side
This replaces the .then() keyword. 
The async keyword is required to allow the await keyword

How can you use fetch to save the state of your web application in a robust way? (and not on the user's machine)

How are promises different from callbacks?
A key difference between the two is when using the callback approach, we’d normally just pass a callback into a function that would then get called upon completion in order to get the result of something. In promises, however, you attach callbacks on the returned promise object.

### Try catch
The try...catch statement marks a try block and a catch block. If the code in the try block throws an exception then the code in the catch block will be executed.

Consider the code below:
```
try {
  try_statements
}
catch (exception_var) {
  catch_statements
}
```
`try_statements` is executed 
`catch_statements` is executed if `exception_var` is thrown
