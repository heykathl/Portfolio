# Domain Modelling

* Process of modeling out code to see what it would look like prior writing the code.
* Higher level thinking than TTD

## Learning Objectives
1. Understand why we would use multiple objects in our programs
2. Understand how diagramming could support our understanding of a problem
3. Use diagramming as a technique to inform how we might design our program before writing code

### What is a domain?
* Collection of names, entities and properties relevant to a specific environment 

### What is an object?
* Collection of properties and methods
* Represents a single piece of data and contains logical entity that can be used
* Class of objects
* Stored in the program
* Has capabilities and functionality. Eg. strings have different functionality to arrays
* Complex construct
* State (attributes) and behaviour (methods or actions)
* Create many objections that have their own identity
* Created from same ‘blueprint’ (class)
 
### Why do we use multiple objects in our program?
* Objects can be shared and communicate with each other
* A way of thinking about the task at hand
* Store discrete data
* Conceptualize multiple versions of the class
* SRP - makes it easier to change
* Reuse code to ensure it is DRY and have cohesion
* Easier to test and debug by isolation

### Why do we use multiple classes of objects in our programs?
* Breaking features up
* Maintainable
* Different classes of objections have different properties
* Organization
* Single Responsibility Principle (this class is only responsible to these specific properties)
* Encapsulation - don’t want all methods to be public, allow certain internals from the public
* Not included by default - functionality 
* Interact between objects

### Unified Markup Language (UML) Class Diagrams

#### Exercise 1:
Given these user stories:

```
As a coach,
So that I know who I am coaching,
I would like to record students names
```
```
As a coach,
So that I can track attendance,
I would like a student to be able to sign in and sign out
```
```
As a coach,
So that I can deliver the course,
I would like to add a student to the cohort
```
```
As a coach,
So that I can see who is in my cohort,
I would like to see a list of students in the cohort
```
```
As a coach,
So that I know how many students are in,
I would like a count of how many students are signed in
```

Complete a domain model for these requirements.

<img width="640" alt="Screen Shot 2022-06-06 at 7 07 22 pm" src="https://user-images.githubusercontent.com/74867241/172219808-e11320e2-86b2-4604-8060-02b0bf98ac4e.png">

* Avoid two way dependency between classes
* Avoid duplicating (Single source of truth)
* Student class can operate on its own, doesn’t depend on cohort

#### Exercise 2:
Taking a look at these user stories:

What would a domain diagram for these user stories look like?

```
As a librarian
So that the public can know which books we have on offer
I would like a book to have a title and an author
```

```
As a librarian
So that I can properly represent the books we have
I would like to add a book to the library
```

```
As a librarian
So that the public knows all the books in the library
I would like to list all books in the library
```

```
As a librarian
So that I can know if a book needs to be replaced
I would like to be able to mark a book as damaged
```

```
As a librarian
So that I know how many books need to be replaced
I would like to count how many books are damaged in the library
```

```
As a librarian
So that the public know what books titles are written by their favourite author
I would like the library to list all book titles by a specific author
```

<img width="642" alt="Screen Shot 2022-06-06 at 7 08 06 pm" src="https://user-images.githubusercontent.com/74867241/172219930-1bb216b1-3018-4668-b94b-07f2e03fb64c.png">

