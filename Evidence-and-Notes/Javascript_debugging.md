# Debugging in JavaScript

## Learning objective

* Building the skills that let you learn a new language and its patterns. 
* Practice a bunch of different ways of following the flow and getting visibility in JavaScript.

### Following the flow

Understanding which parts of your code are running and in which order.

Very similar to tightening the loop, but with a different goal. Instead of trying to narrow in on one buggy line of code, you're just trying to understand what happens when a piece of code runs.

### Getting visibility

Looking at the data contained in the variables in the code you're trying to understand.

### Exercise

I was presented with a broken code below:

```
class FizzBuzz {
  play(number) {
    let otherNumber = number - 50;
    if (this._isDivisibleBy(15, number)) {
      return 'FizzBuzz';
    } else if (this._isDivisibleBy(20, otherNumber)) {
      return 'Buzz';
    } else {
      return number;
    }
  }

  isDivisibleBy(divisor, number) {
    return theNumber + divisor === 0;
  }
}

new FizzBuzz();

for (let i = 1; i <= 100; i++) {
  console.log(fizzBuzz.play(5));
}
```
I ran `node fizzbuzz.js` to understand what was going wrong and was presented with the following error message:
```
console.log(fizzBuzz.play(5));
              ^

ReferenceError: fizzBuzz is not defined
```
This shows that it does not understand what fizzBuzz is. As shown in the code, there is `new FizzBuzz();` which is not allocated to any variable, however it was used in the for loop. I amended this to `const fizzBuzz = new Fizzbuzz();`. I ran node and was presented with another error (this meant that this error was fixed):
```
if (this._isDivisibleBy(15, number)) {
             ^

TypeError: this._isDivisibleBy is not a function 
```
This looks like the isDivisibleBy function has not been consistently named with an underscore (variables with underscores should be treated as if it's private, although it is not. This was used prior to the introduction of the #). By adding the _ in front of the isDivisibleBy function, I was presented with another error message: 
```
return theNumber + divisor === 0;
    ^

ReferenceError: theNumber is not defined
```
`theNumber` is not associate with anything, in particular the parameter being passed in to the isDivisibleBy function. This has been amended to `number` and as I ran node, a list of the number 5 was printed out. I knew this meant that the for loop was not being executing it the way I wanted it to. 

```
const fizzBuzz = new FizzBuzz();

for (let i = 1; i <= 100; i++) {
  console.log(fizzBuzz.play(5));
}
```
As I had created a new instnace of the FizzBuzz class, I could have passed the number 5 as an argument, which will call on the play method. The `console.log` within the for loop will need to print `i` which is the iteration of 1-100. 

The final code looks like this:
```
class FizzBuzz {
  play(number) {
    // let otherNumber = number - 50;
    if (this._isDivisibleBy(15, number)) {
      return 'FizzBuzz';
    } else if (this._isDivisibleBy(5, number)) {
      return 'Buzz';
    } else if (this._isDivisibleBy(3, number)) {
      return 'Fizz';
    } else {
      return number;
    }
  }
  
  _isDivisibleBy(divisor, number) {
    return number % divisor === 0;
  }
}

const fizzBuzz = new FizzBuzz(5);

for (let i = 1; i <= 100; i++) {
  console.log(fizzBuzz.play(i));
}  
```   
