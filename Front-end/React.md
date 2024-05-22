# React Basics

React is an Open Source view library created and maintained by Facebook. 
It's a great tool to render the User Interface (UI) of modern web applications.
React uses a syntax extension of JavaScript called JSX that allows you to write HTML directly within JavaScript. 
This has several benefits. 

It lets you use the full programmatic power of JavaScript within HTML, and helps to keep your code readable. 
For the most part, JSX is similar to the HTML that you have already learned, however there are a few key differences that will be covered throughout these challenges.
For instance, because JSX is a syntactic extension of JavaScript, you can actually write JavaScript directly within JSX. 
To do this, you simply include the code you want to be treated as JavaScript within curly braces: `{ 'this is treated as JavaScript code' }`. 
Keep this in mind, since it's used in several future challenges.

However, because JSX is not valid JavaScript, JSX code must be compiled into JavaScript. 
The transpiler **Babel** is a popular tool for this process. 

## Create a Complex JSX Element

One important thing to know about nested JSX is that it must return a single element.
This one parent element would wrap all of the other levels of nested elements.
For instance, several JSX elements written as siblings with no parent wrapper element will not transpile.

**Valid JSX**
```Javascript
<div>
  <p>Paragraph One</p>
  <p>Paragraph Two</p>
  <p>Paragraph Three</p>
</div>
```

**Invalid JSX**
```Javascript
<p>Paragraph One</p>
<p>Paragraph Two</p>
<p>Paragraph Three</p>
```

## Comments in JSX

JSX is a syntax that gets compiled into valid JavaScript. 
Sometimes, for readability, you might need to add comments to your code. 
Like most programming languages, JSX has its own way to do this.

To put comments inside JSX, you use the syntax `{/* Comment */}` to wrap around the comment text.

## Rendering

So far, you've learned that JSX is a convenient tool to write readable HTML within JavaScript. 
With React, we can render this JSX directly to the HTML DOM using React's rendering API known as **ReactDOM**.

ReactDOM offers a simple method to render React elements to the DOM which looks like this: `ReactDOM.render(componentToRender, targetNode)`, 
where the first argument is the React element or component that you want to render, 
and the second argument is the DOM node that you want to render the component to.

As you would expect, `ReactDOM.render()` must be called after the JSX element declarations, just like how you must declare variables before using them.

The code editor has a simple JSX component. 
Use the `ReactDOM.render()` method to render this component to the page. 
You can pass defined JSX elements directly in as the first argument and use `document.getElementById()` to select the DOM node to render them to. 

## Classes in JSX

So far, it may seem that HTML and JSX are exactly the same.

One key difference in JSX is that you can no longer use the word class to define HTML classes. 
This is because class is a reserved word in JavaScript. 
Instead, JSX uses **className**.

In fact, the naming convention for all HTML attributes and event references in JSX become **camelCase**. 
For example, a click event in JSX is **onClick**, instead of onclick. Likewise, onchange becomes **onChange**.
While this is a subtle difference, it is an important one to keep in mind moving forward.

## Self-closing tags

Another important way in which JSX differs from HTML is in the idea of the self-closing tag.

In HTML, almost all tags have both an opening and closing tag: `<div></div>`; 
the closing tag always has a forward slash before the tag name that you are closing. 
However, there are special instances in HTML called “_self-closing tags_”, or tags that don’t require both an opening and closing tag before another tag can start.

For example the line-break tag can be written as <br> or as <br />, but should never be written as <br></br>, since it doesn't contain any content.

In JSX, the rules are a little different. 
Any JSX element can be written with a self-closing tag, and every element must be closed. 
The line-break tag, for example, must always be written as `<br />` in order to be valid JSX that can be transpiled. 
A <div>, on the other hand, can be written as <div /> or <div></div>. 
The difference is that in the first syntax version there is no way to include anything in the <div />. 

## Stateless functional components

Components are the core of React. 
Everything in React is a component and here you will learn how to create one.

There are two ways to create a React component. 
The first way is to use a JavaScript function. 
Defining a component in this way creates a **stateless functional component**. 
For now, think of a stateless component as one that can receive data and render it, but does not manage or track changes to that data. 

To create a component with a function, you simply write a JavaScript function that returns either JSX or null. 
One important thing to note is that React requires your function name to begin with a capital letter. 
Here's an example of a stateless functional component that assigns an HTML class in JSX:

```Javascript
const DemoComponent = function() {
  return (
    <div className='customClass' />
  );
};
```
After being transpiled, the `<div>` will have a CSS class of **customClass**.

Because a JSX component represents HTML, you could put several components together to create a more complex HTML page. 
This is one of the key advantages of the component architecture React provides. 
It allows you to compose your UI from many separate, isolated components. 
This makes it easier to build and maintain complex user interfaces.

## Create a React component

The other way to define a React component is with the **ES6 class syntax**. 
In the following example, Kitten extends `React.Component`:
```Javascript
class Kitten extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <h1>Hi</h1>
    );
  }
}
```
This creates an ES6 class Kitten which extends the `React.Component` class. 
So the Kitten class now has access to many useful React features, such as local state and lifecycle hooks. 
Also notice the Kitten class has a constructor defined within it that calls `super()`. 
It uses `super()` to call the constructor of the parent class, in this case `React.Component`. 
The constructor is a special method used during the initialization of objects that are created with the class keyword. 
It is best practice to call a component's constructor with super, and pass props to both. 
This makes sure the component is initialized properly. 
For now, know that it is standard for this code to be included.

## Create a Component with Composition

Now we will look at how we can compose multiple React components together. 
Imagine you are building an app and have created three components: a Navbar, Dashboard, and Footer.

To compose these components together, you could create an App parent component which renders each of these three components as children. 
To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX. 
For example, in the render method you could write:
```Javascript
return (
 <App>
  <Navbar />
  <Dashboard />
  <Footer />
 </App>
)
```
When React encounters a custom HTML tag that references another component (a component name wrapped in `< />` like in this example), it renders the markup for that component in the location of the tag. 
This should illustrate the parent/child relationship between the App component and the Navbar, Dashboard, and Footer.

```Jvascript
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        <ChildComponent />
      </div>
    );
  }
};
```

## Use React to Render Nested Components

Component composition is one of React's powerful features. 
When you work with React, it is important to start thinking about your user interface in terms of components like the App example in the last code snippet. 
You break down your UI into its basic building blocks, and those pieces become the components. 
This helps to separate the code responsible for the UI from the code responsible for handling your application logic. 
It can greatly simplify the development and maintenance of complex projects.

```Javascript
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Fruits = () => {
  return (
    <div>
      <TypesOfFruit />
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
      </div>
    );
  }
};
```

## Compose React Components
As the challenges continue to use more complex compositions with React components and JSX, there is one important point to note. 
Rendering ES6 style class components within other components is no different than rendering the simple components you used in the last few challenges. 
You can render JSX elements, stateless functional components, and ES6 class components within other components.

```Javascript
class Fruits extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h2>Fruits:</h2>
        <NonCitrus />
        <Citrus />
      </div>
    );
  }
};

class TypesOfFood extends React.Component {
  constructor(props) {
     super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits /> 
        <Vegetables />
      </div>
    );
  }
};
```

## Render a Class Component to the DOM

You may remember using the ReactDOM API in an earlier challenge to render JSX elements to the DOM. 
The process for rendering React components will look very similar. 
The past few challenges focused on components and composition, so the rendering was done for you behind the scenes. 
However, none of the React code you write will render to the DOM without making a call to the ReactDOM API.

Here's a refresher on the syntax: `ReactDOM.render(componentToRender, targetNode)`. 
The first argument is the React component that you want to render. 
The second argument is the DOM node that you want to render that component within.

React components are passed into `ReactDOM.render()` a little differently than JSX elements. 
For JSX elements, you pass in the name of the element that you want to render. 
However, for React components, you need to use the same syntax as if you were rendering a nested component, for example `ReactDOM.render(<ComponentToRender />, targetNode)`. 
You use this syntax for both ES6 class components and functional components.

```Javascript
class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        {/* Change code below this line */}
        <Fruits />
        <Vegetables />
        {/* Change code above this line */}
      </div>
    );
  }
};

// Change code below this line
ReactDOM.render(<TypesOfFood />, document.getElementById('challenge-node'));
```

## Pass Props to a Stateless Functional Component

In React, you can pass props, or properties, to child components. 
Say you have an App component which renders a child component called _Welcome_ which is a stateless functional component. 
You can pass Welcome a user property by writing:

```Javascript
<App>
  <Welcome user='Mark' />
</App>
```

```Javascript
const CurrentDate = (props) => {
  return (
    <div>
      <p>The current date is: {props.date}</p>
    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        <CurrentDate date={Date()}/>
      </div>
    );
  }
};
```

## Pass an Array as Props
The last challenge demonstrated how to pass information from a parent component to a child component as props or properties. 
This challenge looks at how arrays can be passed as props. 
To pass an array to a JSX element, it must be treated as JavaScript and wrapped in curly braces.

```Javascript
<ParentComponent>
  <ChildComponent colors={["green", "blue", "red"]} />
</ParentComponent>
```
The child component then has access to the array property colors. 
Array methods such as join() can be used when accessing the property.

```Javascript
const List = (props) => {
  return <p>{props.tasks.join(', ')}</p>
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        <List tasks={["walk cat", "workout"]}/>
        <h2>Tomorrow</h2>
        <List tasks={["walk dog", "play minesweeper"]}/>
      </div>
    );
  }
};
```

## Use Default Props

React also has an option to set default props. 
You can assign default props to a component as a property on the component itself and React assigns the default prop if necessary. 
This allows you to specify what a prop value should be if no value is explicitly provided. 
For example, if you declare `MyComponent.defaultProps = { location: 'San Francisco' }`, you have defined a location prop that's set to the string San Francisco, unless you specify otherwise. 
React assigns default props if props are undefined, but if you pass `null` as the value for a prop, it will remain `null`.

```Javascript
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};

ShoppingCart.defaultProps = {items: 0};
```

## Override Default Prop

```Javascript
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items quantity={10}/>
  }
};
```

## Use PropTypes to Define the Props You Expect

React provides useful _type-checking features_ to verify that components receive props of the correct type. 
For example, your application makes an API call to retrieve data that you expect to be in an array, which is then passed to a component as a prop. 
You can set propTypes on your component to require the data to be of type array. 
This will throw a useful warning when the data is of any other type.

It's considered a best practice to set `propTypes` when you know the type of a prop ahead of time. 
You can define a propTypes property for a component in the same way you defined `defaultProps`. 
Doing this will check that props of a given key are present with a given type. 

Here's an example to require the type function for a prop called handleClick:
```MyComponent.propTypes = { handleClick: PropTypes.func.isRequired }```

In the example above, the `PropTypes.func` part checks that handleClick is a function. 
Adding isRequired tells React that handleClick is a required property for that component. 
You will see a warning if that `prop` isn't provided. Also notice that func represents function. 
Among the seven JavaScript primitive types, function and boolean (written as bool) are the only two that use unusual spelling. 
In addition to the primitive types, there are other types available. For example, you can check that a prop is a React element. 
Please refer to the documentation for all of the options.

_**Note**: As of React v15.5.0, PropTypes is imported independently from React, like this: import PropTypes from 'prop-types';_

```Javascript
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

Items.propTypes = { quantity: PropTypes.number.isRequired }

Items.defaultProps = {
  quantity: 0
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};
```

## Access Props Using this.props

But what if the child component that you're passing a prop to is an ES6 class component, rather than a stateless functional component? 
The ES6 class component uses a slightly different convention to access props.

Anytime you refer to a class component within itself, you use the `this` keyword. 
To access `props` within a class component, you preface the code that you use to access it with `this`. 
For example, if an ES6 class component has a prop called `data`, you write `{this.props.data}` in JSX.

```Javascript
class App extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
            
            <Welcome name="Maksym"/>
            
        </div>
    );
  }
};

class Welcome extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
          <p>Hello, <strong>{this.props.name}</strong>!</p>

        </div>
    );
  }
};
```

## Review Using Props with Stateless Functional Components

These components act like pure functions. 
They accept props as input and return the same view every time they are passed the same props. 

- A **stateless functional component** is any function you write which **accepts props** and **returns JSX**. 
- A **stateless component**, on the other hand, is a class that **extends React.Component**, but **does not use internal state**. 
- Finally, a **stateful component** is a **class component** that does **maintain its own internal state**.
  
You may see stateful components referred to simply as components or React components.

A common pattern is to try to minimize statefulness and to create stateless functional components wherever possible. 
This helps contain your state management to a specific area of your application. 
In turn, this improves development and maintenance of your app by making it easier to follow how changes to state affect its behavior.

```Javascript
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper />
      </div>
    );
  }
};

const Camper = (props) => {
  return (
    <div>
      <p>{props.name}</p>
    </div>
  );
}

Camper.propTypes = {name: PropTypes.string.isRequired};

Camper.defaultProps = {name: 'CamperBot'};
```

## Create a Stateful Component

One of the most important topics in React is state. 
State consists of any data your application needs to know about, that can change over time. 
You want your apps to respond to state changes and present an updated UI when necessary. 
React offers a nice solution for the state management of modern web applications.

You create state in a React component by declaring a state property on the component class in its constructor. 
This initializes the component with state when it is created. 
The state property must be set to a JavaScript object. 
Declaring it looks like this:

```Javascript
this.state = {
 // states
}
```

You have access to the state object throughout the life of your component. 
You can update it, render it in your UI, and pass it as props to child components. 
The state object can be as complex or as simple as you need it to be.
Note that you must create a class component by extending `React.Component` in order to create state like this.

```Javascript
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      firstName : 'Maksym'
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.firstName}</h1>
      </div>
    );
  }
};
```

## Render State in the User Interface

Once you define a component's initial state, you can display any part of it in the UI that is rendered. 
If a component is stateful, it will always have access to the data in state in its render() method. 
You can access the data with `this.state`.

If you want to access a state value within the return of the render method, you have to enclose the value in **curly braces**.

`state` is one of the most powerful features of components in React. 
- It allows you to track important data in your app and render a UI in response to changes in this data. 
- If your data changes, your UI will change.
React uses what is called a virtual DOM, to keep track of changes behind the scenes. 
When state data updates, it triggers a re-render of the components using that data - including child components that received the data as a prop. 
React updates the actual DOM, but only where necessary. This means you don't have to worry about changing the DOM. 
You simply declare what the UI should look like.

Note that if you make a component stateful, no other components are aware of its state. 
Its state is completely encapsulated, or local to that component, unless you pass state data to a child component as props. 
This notion of encapsulated state is very important because it allows you to write certain logic, then have that logic contained and isolated in one place in your code.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

## Render State in the User Interface Another Way

There is another way to access state in a component. 
In the `render()` method, before the return statement, you can write JavaScript directly. 
For example, you could declare functions, access data from state or props, perform computations on this data, and so on. 
Then, you can assign any data to variables, which you have access to in the return statement.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    const name = this.state.name;
    return (
      <div>
        <h1>{name}</h1>
      </div>
    );
  }
};
```

## Set State with this.setState

There is also a way to change the component's state. 
React provides a method for updating component state called `setState`. 
You call the `setState` method within your component class like so: `this.setState()`, passing in an object with key-value pairs. 
The keys are your state properties and the values are the updated state data. 
For instance, if we were storing a username in state and wanted to update it, it would look like this:

```Javascript
this.setState({
  username: 'Lewis'
});
```

React expects you to never modify state directly, instead always use `this.setState()` when state changes occur. 
Also, you should note that React may batch multiple state updates in order to improve performance. 

What this means is that state updates through the `setState` method can be **asynchronous**. 
There is an alternative syntax for the `setState` method which provides a way around this problem. 
This is rarely needed but it's good to keep it in mind! 

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      name: 'React Rocks!'
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

## Bind 'this' to a Class Method

In addition to setting and updating state, you can also define methods for your component class. 
A class method typically needs to use the `this` keyword so it can access properties on the class (such as state and props) inside the scope of the method. 
There are a few ways to allow your class methods to access `this`.

One common way is to explicitly bind `this` in the constructor so `this` becomes bound to the class methods when the component is initialized. 
You may have noticed the last challenge used `this.handleClick = this.handleClick.bind(this)` for its `handleClick` method in the constructor. 
Then, when you call a function like `this.setState()` within your class method, this refers to the class and will not be `undefined`.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      text: "Hello"
    };
    
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      text: "You clicked!"
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.text}</h1>
      </div>
    );
  }
};
```

## Use State to Toggle an Element

Sometimes you might need to know the previous state when updating the state. 
However, state updates may be asynchronous - this means React may batch multiple `setState()` calls into a single update. This means you can't rely on the previous value of `this.state` or `this.props` when calculating the next value. 
So, you should not use code like this:

```Javascript
this.setState({
  counter: this.state.counter + this.props.increment
});
```

Instead, you should pass `setState` a function that allows you to access state and props. 
Using a function with setState guarantees you are working with the most current values of state and props. 
This means that the above should be rewritten as:

```Javascript
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

You can also use a form without props if you need only the state:

```Javascript
this.setState(state => ({
  counter: state.counter + 1
}));
```

Note that you have to wrap the object literal in parentheses, otherwise JavaScript thinks it's a block of code.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    this.toggleVisibility = this.toggleVisibility.bind(this);
  }
  
  toggleVisibility() {
    this.setState(prevState => ({
      visibility: !prevState.visibility
    }));
  }

  render() {
    return (
      <div>
        <button onClick={this.toggleVisibility}>Click Me</button>
        {this.state.visibility && <h1>Now you see me!</h1>}
      </div>
    );
  }
}
```

## Write a Simple Counter

You can design a more complex stateful component by combining the concepts covered so far. 
These include initializing state, writing methods that set state, and assigning click handlers to trigger these methods.

```Javascript
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    this.increment = this.increment.bind(this);
    this.decrement = this.decrement.bind(this);
    this.reset = this.reset.bind(this);
  }

  increment() {
    this.setState(prevState => ({
      count: prevState.count + 1
    }));
  }

  decrement() {
    this.setState(prevState => ({
      count: prevState.count - 1
    }));
  }

  reset() {
    this.setState({
      count: 0
    });
  }

  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```

## Create a Controlled Input

Your application may have more complex interactions between state and the rendered UI. 
For example, form control elements for text input, such as `input` and `textarea`, maintain their own state in the DOM as the user types. 
With React, you can move this mutable state into a React component's state. 
The user's input becomes part of the application state, so React controls the value of that input field. 
Typically, if you have React components with input fields the user can type into, it will be a controlled input form.

```Javascript
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this);
  }

  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }

  render() {
    return (
      <div>
        <input value={this.state.input} onChange={this.handleChange}/>
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```

## Create a Controlled Form

The last challenge showed that React can control the internal state for certain elements like input and textarea, which makes them controlled components. This applies to other form elements as well, including the regular HTML form element.

```Javascript
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: ''
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    
    this.setState({
      input: event.target.value
    });
  }

  handleSubmit(event) {
    event.preventDefault();
    this.setState(prevState => ({
      submit: prevState.input
    }));
  }

  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          <input type='form' value={this.state.input} onChange={this.handleChange}/>
          <button type='submit' onClick={this.handleSubmit}>Submit!</button>
        </form>
  	  <h1>{this.state.submit}</h1>
      </div>
    );
  }
}
```

