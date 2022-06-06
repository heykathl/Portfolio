# HTTP Process Modeling

## What is process modeling?
A process model is a diagram/performance/[something else] that demonstrates how a process works for a web page and how it interacts between the client and server.

## Learning objectives
- Define process modeling as a tool to describe and understand a process.
- Use process modeling to further your understanding of HTTP requests and responses.

## Why model a process?
- Quick way to figure out and cement understanding of how a process works.
- Quicker than writing the code that enacts the process.
- Easier to iterate on a process model than the code that enacts the process.
- Easier to add detail to a process model than to add it to code.
- Great way to communicate and discuss a process with another person.

## What is HTTP?
- Protocol to exchange between client and server
- Get and Post queries
- Used through the browser and terminal
- Used to send HTML, CSS, images, raw data, audio etc.
- Request and response
- Send metadata (information about the data)

## Exercises
Process model the following scenarios.

* The order that things happen in.
* The HTTP requests and the data they carry. (Resources for this at the bottom of this README.)
* The HTTP responses and the data they carry. (Resources for this at the bottom of this README.)
* The movement of requests between client and server.
* Mouse clicks or other user actions.
* What is displayed in the browser.

Visiting the home page
A user visits `https://makers-cats.herokuapp.com/` and they are shown this HTML:
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Req/Res</title>
  </head>
  <body>
    <ul>
      <a href="list.html">a list</a>
      <a href="cats.html">a cat pic</a>
    </ul>
  </body>
</html>

```

Home page with typo
A user tries to visit `https://makers-cats.herokuapp.com/`, but mistypes the URL as `https://makers-rats.herokuapp.com/` in their browser.
At first they don't see the page they expect. When they fix their typo to the correct home page URL, they are shown this HTML:

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Req/Res</title>
  </head>
  <body>
    <ul>
      <a href="list.html">a list</a>
      <a href="cats.html">a cat pic</a>
    </ul>
  </body>
</html>

```

Cat page
A user clicks the `a cat pic` link and is shown this HTML:

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>a cat</title>
  </head>
  <body>
    <img src='cat.jpg'>
  </body>
</html>

```

Don't forget to model the `cat.jpg` request and response.

Mailing list page
A user clicks the `list` link and is shown this HTML:

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>A list</title>
  </head>
  <body>
    <form action="thanks.html" method="POST">
      <input type="text" name="email">
      <input type="submit">
    </form>
  </body>
</html>
```

The user fills in their email address and clicks the submit button.
The user is sent to the `thanks.html` page and is shown this HTML:

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Thanks page</title>
  </head>
  <body>
    <h1>Thanks!</h1>
  </body>
</html>
```

I've process modelled the scenarios as shown below:
<img width="654" alt="Screen Shot 2022-06-06 at 7 13 06 pm" src="https://user-images.githubusercontent.com/74867241/172220706-c43e84d7-46eb-4ccd-bdfd-5579dde42747.png">
