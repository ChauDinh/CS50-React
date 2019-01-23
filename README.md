
Note:
Hello there! This project is what I've learnt from CS50 Beyond series published by Harvard University. You can check for more infomation on the Youtube channel CS50.

# REACT

* Declarative
* JSX
* Components
* State

## What we will cover?

* What is imperadive programming? and What is declarative programming?

Imperative programming is that we write codes to tell the web applications what we want to do, including insert, manipulate in a particular way, etc. On the other hand, declarative programming is that what we want to our application look like! Or how the application should work. And React is used to take care of figuring out what the application should do in order to make the look that what we want initially. 

In particular, to achieve that goal, there are number of tools that React is going to use. The first is JSX.

* What is JSX?

In JSX, we can treat html elements as the value like string, function, array, etc. For instance
```
const foo = <h1>Hello, world!</h1>
```

In this case, an html code (h1 tag) is assigned as the value of the variable called foo.

* What is ReactDOM?

ReactDOM is going to take care of taking components (we will mention about Component below) that we've created and inserting them into the webpage, particularly the DOM that we want. 

* What is Babel?

We using this package in React development cause most web browsers don't fully support JSX. So we need to translate our codes into vanilla javascript code so that they can understand, Babel is the tool for that action. 

Here are three script for React, ReactDOM and Babel that we'll later

```
<script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```



