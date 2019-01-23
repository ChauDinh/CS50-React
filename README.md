
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

Here are three script for React, ReactDOM and Babel that we'll use later

```
<script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

* What is Component?

Components come when we think about web applications and devide it into small parts that make it up. For example, navbar components, search components, list components, about components, etc. Here is an example of writing a component in React
```
class Hello extends Component {
 render() {
  return (
   <div>
    <h1>Hello, world!</h1>
    ...
   </div>
  )
 }
}
```
And then, we want to render the class Hello (in this case, that also mean the text "Hello, world") into the div having an id named "root" of our DOM.

```
...
ReactDOM.render(<Hello />, document.getElementById("root"));
```
extends Component or extends React.Component is that Hello class is a React Component. 
Every component is going to need a render() function, describing what the component looks like. In this case it has a "Hello, world!" text at the first line. 

Another thing that we can do with components is we can nest components with each other. Here is an example:

```
...
class Hello extends React.Component {
 ...
}

class App extends React.Component {
 render() {
  return (
   <div>
    <Hello />
    <Hello />
   </div>
  )
 }
}

ReactDOM.render(<App />, document.getElementById("root"));
```

