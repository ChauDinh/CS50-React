
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
```jsx
const foo = <h1>Hello, world!</h1>
```

In this case, an html code (h1 tag) is assigned as the value of the variable called foo.

* What is ReactDOM?

ReactDOM is going to take care of taking components (we will mention about Component below) that we've created and inserting them into the webpage, particularly the DOM that we want. 

* What is Babel?

We using this package in React development cause most web browsers don't fully support JSX. So we need to translate our codes into vanilla javascript code so that they can understand, Babel is the tool for that action. 

Here are three script for React, ReactDOM and Babel that we'll use later

```html
<script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

* What is Component?

Components come when we think about web applications and divide it into small parts that make it up. For example, navbar components, search components, list components, about components, etc. Here is an example of writing a component in React
```js
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

```js
...
ReactDOM.render(<Hello />, document.getElementById("root"));
```
extends Component or extends React.Component is that Hello class is a React Component. 
Every component is going to need a render() function, describing what the component looks like. In this case it has a "Hello, world!" text at the first line. 

Another thing that we can do with components is we can nest components with each other. Here is an example:

```js
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
* What is state?

State is, when speaking about application state, anything that needs to live and be modified in the browser. There are two kind of state, one is Entity state - data retrieved from backend and the other is View state - which is used when we open up a modal or switch a box from preview to edit mode. We will talk about state more.

### Local state in React

Let's consider the codes from file `counter.html`. The Counter component has a count property in local state object defined with the value 0 initially. Notice that we cannot change/alter the state directly. That would be a direct mutation. Instead, we have to use a React API named `this.setState()` method. 

```jsx
class Counter extends React.Component {
   constructor(props) {
    super(props);
    this.state = {
     count: 0
    };
    this.increment = this.increment.bind(this);
    this.decrement = this.decrement.bind(this);
   }

   decrement() {
    this.setState(oldState => ({
     count: oldState.count - 1
    }));
   }

   increment() {
    this.setState(oldState => ({
     count: oldState.count + 1
    }));
   }
   ...
}
```
Now, we have a button `onClick` handler involking the class methods to alter the state by either increment or decrement

```jsx
class Counter extends React.Component {
   constructor(props) {
    ...
   }
   decrement() {
    ...
   }
   increment() {
    ...
   }

   render() {
    return(
     <div>
      <h1>{this.state.count}</h1>
      <button onClick={this.decrement}>Decrement</button>
      <button onClick={this.increment}>Increment</button>
     </div>
    )
   }
  }
```
The update functionality with `this.setState()` is performing a shallow merge of objects. So, what does a shallow merge mean?

### Shallow Merge

Let look at the code below

```jsx
this.state = {
   authors: [...],
   articles: [...]
};
```
Imagine we only need to update the state partly, for example the authors by doing the following, the articles property left intact.

```jsx
updateAuthor() {
   this.setState({
      authors: [
         { name: "Leslie", id: "1" }
      ]
   })
}
```

One of the interestings of React is that React knows exactly what we want to be updated - in this case, React does not touch the articles property. In other words, it simplifies the local state management by not always keeping an eye on all properties in the local state. That's a shallow merge.

### Statefull and Stateless Components
As we discussed above, we use Babel as class component in React only be used in ES6. Local state can only be used in React class. The component becomes a <b>stateful component</b> when the state is used. Otherwise, it can be called <b>stateless component</b>. 

```jsx
import React from "react"

function CounterPresenter(props) {
   return (
      <div>
         <p>{props.counter}</p>
         <button onClick={props.onIncrement}>Increment</button>
         <button onClick={props.onDecrement}>Decrement</button>
      </div>
   );
}
```
The CounterPresenter is actually called functional stateless component since it has no state - stateless. In a stateless component, we can only pass props from a parent component. Additionally, callbacks could be passed down to alert the state in parent component. 

In this case, two callbacks `onIncrement` and `onDecrement` would be used for the buttons. However, the stateless component itself is not aware whether the passed properties are state, props or something detrived properties. 


```jsx
class Counter extends React.Component {
   constructor(props) {...};

    this.increment = this.increment.bind(this);
    this.decrement = this.decrement.bind(this);
   }
...
}
```
These two lines in `constructor()` function will tell React what the passed properties come from.

Ok, I think this is enough for the basic of React. For more, we can read in the book called <b>"Taming the State in React"</b>.

### React Todo Tricks

Like learning other frameworks, or libraries, the first project we want to try is building a todoapp allowing us add/update/delete tasks. Here are some tips for us before starting.
* Copying a list

```js
const originalList = [1, 2, 3, 4, 5];
const copyList = [...originalList]; 
```
* Copying a list, then adding something into the end
```js
const originalList = [1, 2, 3, 4, 5];
const copyList = [...originalList, 6];
```
* Delete something on a list
```js
const originalList = [1, 2, 3, 4, 5];

originalList.splice(3, 1) // originalList is now [1, 2, 3, 5]
```
