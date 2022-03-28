# JavaScript Fundamentals

### Variables
Declaring variables with the use of 
```
const
let
```

### [Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#defining_functions)
A function definition (also called a function declaration, or function statement) consists of the function keyword, followed by:

* The name of the function.
* A list of parameters to the function, enclosed in parentheses and separated by commas.
* The JavaScript statements that define the function, enclosed in curly brackets, {...}.

##### Scope
Variables defined inside a function cannot be accessed from anywhere outside the function, because the variable is defined only in the scope of the function. However, a function can access all variables and functions defined inside the scope in which it is defined.
A function defined in the global scope can access all variables defined in the global scope. A function defined inside another function can also access all variables defined in its parent function, and any other variables to which the parent function has access.

##### Syntax
Preferred way of writing functions
```
const printMessage = () => console.log('hello');
```

Other ways it could be written
```
const printMessage = function(){
  console.log('hello');}

function printMessage(params) {
  console.log(params);
}
```

##### Calling functions from within a function
```
const notifyByEmail = (email) => {
  return `Email sent to ${email}`;
}

const notifyByText = (phoneNumber) => {
  return `Text sent to ${phoneNumber};`
}

const notify = (contact) => {
  return contact;
}

console.log(notify(notifyByEmail('sam@example.com'));
console.log(notify(notifyByText('123456780')));
```

### Conditions
```
const getNumberSign = (number) => {
  if (number === 0){
    return "zero";
  } else if (number >= 1) {
      return "positive";
  } else {
      return "negative";
  }
}
```

Can be written as follows:
```
const getNumberSign2 = (number) => {
  if (number === 0) return "zero";
  else if (number >= 1) return "positive";
  else return "negative";
}
console.log(getNumberSign(0));

const isValidLength = (phoneNumber) => {
  const validLength = 10;
  if (phoneNumber.length === validLength) return true;
  else return false;
}

console.log(isValidLength('1234567891'));
```
* === compares data types as well

### Arrays
##### Appending arrays
Mutative - This will change the original array
* array.push(newItem)
* array.splice(startIndex, deleteCount, items)
* array[array.length] = newItem

Non-mautative - This will create a new array and the original array remains unchanged.
* array.concat(newItem)
* spread - newArray = [...array, ...array2]

When to mutate and when not to?
If the original array is still needed somewhere else then you don't want to mutate it. If it is not needed, you can mutate it directly, which is usually faster than creating a copy.
Note: The idea of immutability is often preferred as it's considered a good practice to avoid side effects -- which is the foundation of functional programming and producing pure functions.