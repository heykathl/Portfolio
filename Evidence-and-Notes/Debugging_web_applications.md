# Debugging Web Applications

## Learning Objectives
* Use your understanding of how a web application works to debug across the stack.
* Follow the flow of a web application to:
  * find the source of a bug
  * find a way to fix the bug

<img width="645" alt="Screen Shot 2022-06-06 at 10 44 32 pm" src="https://user-images.githubusercontent.com/74867241/172254409-56e6131e-e5d9-44e0-84b1-0f5c1e872293.png">

### What are the ways in which we can get visibility over our code?
* Read stack trace
  * Reading and breaking down error messages
  * Start with unit tests (smallest bug first)
* Feature testing in irb 
* Writing useful tests
* Follow the data flow / diagram
* Read the unit or feature tests to get a better understanding of what the code is doing
* Add empty lines between each components
  * To see individual parts of the code
* Print parts of the code
  * Printing each line to see what each line does (step by step)
  * Breaking/splitting up single lines of code - a line which is doing multiple things
  * Print things out with ‘p’ +
* Commenting out lines until tests all passed, and re-add the lines one by one
* Review what’s changed since previous working versions
* Rubber duck debugging - explain the problem out loud
* Understand and explain what each line is doing
* Run a piece of code elsewhere eg. irb, replit
* Check your assumptions