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

Scope
Variables defined inside a function cannot be accessed from anywhere outside the function, because the variable is defined only in the scope of the function. However, a function can access all variables and functions defined inside the scope in which it is defined.
A function defined in the global scope can access all variables defined in the global scope. A function defined inside another function can also access all variables defined in its parent function, and any other variables to which the parent function has access.

Syntax
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

Calling functions from within a function
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
Appending arrays
Mutative - This will change the original array
* array.push(newItem)
* array.splice(startIndex, deleteCount, items)
* array[array.length] = newItem

Non-mutative - This will create a new array and the original array remains unchanged.
* array.concat(newItem)
* spread - newArray = [...array, ...array2]

When to mutate and when not to?
If the original array is still needed somewhere else then you don't want to mutate it. If it is not needed, you can mutate it directly, which is usually faster than creating a copy.
Note: The idea of immutability is often preferred as it's considered a good practice to avoid side effects -- which is the foundation of functional programming and producing pure functions.

Chaining array methods - filter and map

```
const searchCandies = (letters, price) => {
  return candies = [
    
{ name: 'Aero', price: 1.99 },
    { name: 'Skitties', price: 2.99 },
    { name: 'Mars', price: 1.49 },
  ]
    .filter(item => item.price <= price )
    .filter(item => item.name.toLowerCase().startsWith(letters.toLowerCase()))
    .map(item => {
      return item.name
    })
}

console.log(searchCandies('Ma', 4));
```

Methods that loop through arrays
* Filter method ( filter())
* Map method ( map())
* Reduce method ( reduce())
* Find method ( find())
* Sort method ( sort())

### Objects and properties
A property of an object can be explained as a variable that is attached to the object. Object properties are basically the same as ordinary JavaScript variables, except for the attachment to objects. The properties of an object define the characteristics of the object. 

Creating a new object:
```
const myCar = new Object();
myCar.make = 'Ford';
myCar.model = 'Mustang';
myCar.year = 1969;
```

This can also be written using an object initialiser:
```
const myCar = {
  make: 'Ford',
  model: 'Mustang',
  year: 1969
};
```

Accessing the properties can be done using the dot notation or brackets:
```
objectName.propertyName;
myCar.make = 'Ford'

objectName["propertyName"]
myCar['make'] = 'Ford'
```

When working with dot notation, property identifies can only be alphanumeric (and _ and $). Properties can’t start with a number.

When working with bracket notation, property identifiers only have to be a String. They can include any characters, including spaces. Variables may also be used as long as the variable resolves to a String. This means there are fewer limitations when working with bracket notation. We can now have spaces in our strings, and can even start strings with numbers. We can now use variables to access properties in an object. It’s important the variable you are using references a String.

Dot notation:
* Property identifies can only be alphanumeric (and _ and $)
* Property identifiers cannot start with a number.
* Property identifiers cannot contain variables.
* OK — obj.prop_1, obj.prop$
* Not OK — obj.1prop, obj.prop name

Bracket notation:
* Property identifiers have to be a String or a variable that references a String.
* It is okay to use variables, spaces, and Strings that start with numbers
* OK — obj["1prop"], obj["prop name"]

### Classes
Classes work in a similar way to other languages, they are declared with methods — and perhaps attributes — and can be instantiated when creating instances. They are a kind of function. 
```
class User {
  constructor(name) {
    this.name = name;
  };

  getName() {
    return this.name;
  };

  getIntroduction() {
    return `Hi, my name is ${this.name}`;
  };
};

let user = new User('Jim')
user.getName()
<!-- this will return Jim -->
user.getIntroduction() 
<!-- this will return Hi, my name is Jim -->

```
The constructor method is a special method of a class for creating and initializing an object instance of that class. This is similar to the initialize method within Ruby. A constructor enables you to provide any custom initialization that must be done before any other methods can be called on an instantiated object.

### JEST tests
Mocking
```
const candy = ["Mars", 5.99;]
candy.getPrice(); // '5.99'

// let's now mock .getPrice()

const candyDouble = { getPrice: () => 5.99 };

// so we can call candyDouble.getPrice()
// which means it's a drop-in replacement for "real" object,
// *as long as we only want* to use .tgetPrice()) on it.
```

### Difference between Javascript and Ruby





