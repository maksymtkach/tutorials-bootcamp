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

## Pass State as Props to Child Components

You may be wondering where those props come from. 
A common pattern is to have a stateful component containing the state important to your app, that then renders child components. 
You want these components to have access to some pieces of that state, which are passed in as props.

For example, maybe you have an App component that renders a Navbar, among other components. 
In your App, you have state that contains a lot of user information, but the Navbar only needs access to the user's username so it can display it. 
You pass that piece of state to the Navbar component as a prop.

This pattern illustrates some important paradigms in React. 
- The first is **unidirectional data flow**. 
State flows in one direction down the tree of your application's components, from the stateful parent component to child components. 
The child components only receive the state data they need.
 
- The second is that complex stateful apps can be broken down into just a few, or maybe a single, stateful component.
The rest of your components simply receive state from the parent as props, and render a UI from that state.
It begins to create a separation where state management is handled in one part of code and UI rendering in another.
This principle of separating state logic from UI logic is one of React's key principles.

When it's used correctly, it makes the design of complex, stateful applications much easier to manage.

```Javascript
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'CamperBot'
    }
  }
  render() {
    return (
       <div>
         <Navbar name={this.state.name}/>
       </div>
    );
  }
};

class Navbar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
    <div>
      <h1>Hello, my name is: {this.props.name}</h1>
    </div>
    );
  }
};
```

## Pass a Callback as Props

You can pass state as props to child components, but you're not limited to passing data. 
You can also pass handler functions or any method that's defined on a React component to a child component. 
**This is how you allow child components to interact with their parent components.** 
You pass methods to a child just like a regular prop. 
It's assigned a name and you have access to that method name under this.props in the child component.

```Javascript
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        <GetInput input={this.state.inputValue} handleChange={this.handleChange}/>
        <RenderInput input={this.state.inputValue} />
       </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input
          value={this.props.input}
          onChange={this.props.handleChange}/>
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```

_You will be able to type in the input field in the GetInput component, which then calls the handler method in its parent via props. 
This updates the input in the state of the parent, which is passed as props to both children. 
Observe how the data flows between the components and how the single source of truth remains the state of the parent component. 
Admittedly, this example is a bit contrived, but should serve to illustrate how data and callbacks can be passed between React components._

## Use the Lifecycle Method componentWillMount

React components have several special methods that provide opportunities to perform actions at specific points in the lifecycle of a component. 
These are called **lifecycle methods**, or **lifecycle hooks**, and allow you to catch components at certain points in time. 
This can be before they are rendered, before they update, before they receive props, before they unmount, and so on. 
Here is a list of some of the main lifecycle methods: `componentWillMount()` `componentDidMount()` `shouldComponentUpdate()` `componentDidUpdate()` `componentWillUnmount()`.

**Note:** The `componentWillMount` Lifecycle method will be deprecated in a future version of 16.X and removed in version 17.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  componentWillMount() {
    console.log("The component is going to be rendered in the DOM");
  }
  render() {
    return <div />
  }
};
```

## Use the Lifecycle Method componentDidMount

Most web developers, at some point, need to call an API endpoint to retrieve data. 
If you're working with React, it's important to know where to perform this action.

The best practice with React is to place API calls or any calls to your server in the lifecycle method `componentDidMount()`. 
This method is called after a component is mounted to the DOM. 
Any calls to `setState()` here will trigger a re-rendering of your component. 
When you call an API in this method, and set your state with the data that the API returns, it will auto trigger an update once you receive the data.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      activeUsers: null
    };
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({
        activeUsers: 1273
      });
    }, 2500);
  }
  render() {
    return (
      <div>
        <h1>Active Users: {this.state.activeUsers}</h1>
      </div>
    );
  }
}
```

## Add Event Listeners

The `componentDidMount()` method is also the best place to attach any event listeners you need to add for specific functionality. 
React provides a synthetic event system which wraps the native event system present in browsers. 
This means that the synthetic event system behaves exactly the same regardless of the user's browser - 
even if the native events may behave differently between different browsers.

React's synthetic event system is great to use for most interactions you'll manage on DOM elements. 
However, if you want to attach an event handler to the document or window objects, you have to do this directly.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      message: ''
    };
    this.handleEnter = this.handleEnter.bind(this);
    this.handleKeyPress = this.handleKeyPress.bind(this);
  }
  componentDidMount() {
    document.addEventListener('keydown', this.handleKeyPress);
  }
  componentWillUnmount() {
    document.removeEventListener('keydown', this.handleKeyPress);
  }
  handleEnter() {
    this.setState((state) => ({
      message: state.message + 'You pressed the enter key! '
    }));
  }
  handleKeyPress(event) {
    if (event.keyCode === 13) {
      this.handleEnter();
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.message}</h1>
      </div>
    );
  }
};
```

## Optimize Re-Renders with shouldComponentUpdate

So far, if any component receives new state or new props, it re-renders itself and all its children. 
This is usually okay. 
But React provides a lifecycle method you can call when child components receive new state or props, 
and declare specifically if the components should update or not. 
The method is `shouldComponentUpdate()`, and it takes `nextProps` and `nextState` as parameters.

This method is a useful way to optimize performance. 
For example, the default behavior is that your component re-renders when it receives new props, even if the props haven't changed. 
You can use `shouldComponentUpdate()` to prevent this by comparing the props. 
The method must return a boolean value that tells React whether or not to update the component. 
You can compare the current props `(this.props)` to the next props `(nextProps)` to determine if you need to update or not, 
and return true or false accordingly.

```Jvascript
class OnlyEvens extends React.Component {
  constructor(props) {
    super(props);
  }
  shouldComponentUpdate(nextProps, nextState) {
    console.log('Should I update?');
    return nextProps.value % 2 === 0;
  }
  componentDidUpdate() {
    console.log('Component re-rendered.');
  }
  render() {
    return <h1>{this.props.value}</h1>;
  }
}

class Controller extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 0
    };
    this.addValue = this.addValue.bind(this);
  }
  addValue() {
    this.setState(state => ({
      value: state.value + 1
    }));
  }
  render() {
    return (
      <div>
        <button onClick={this.addValue}>Add</button>
        <OnlyEvens value={this.state.value} />
      </div>
    );
  }
}
```

## Introducing Inline Styles

There are other complex concepts that add powerful capabilities to your React code. 
But you may be wondering about the more simple problem of how to style those JSX elements you create in React. 
You likely know that it won't be exactly the same as working with HTML because of the way you apply classes to JSX elements.

If you import styles from a stylesheet, it isn't much different at all. 
You apply a class to your JSX element using the className attribute, and apply styles to the class in your stylesheet. 
Another option is to apply inline styles, which are very common in ReactJS development.

You apply inline styles to JSX elements similar to how you do it in HTML, but with a few JSX differences. 
Here's an example of an inline style in HTML:

```html
<div style="color: yellow; font-size: 16px">Mellow Yellow</div>
```

JSX elements use the `style` attribute, but because of the way JSX is transpiled, you can't set the value to a string. 
Instead, you set it equal to a **JavaScript object**. 
Here's an example:

```Javascript
<div style={{color: "yellow", fontSize: 16}}>Mellow Yellow</div>
```

Notice how we camelCase the `fontSize` property? 
This is because React will not accept kebab-case keys in the style object. 
React will apply the correct property name for us in the HTML.

```Javascript
class Colorful extends React.Component {
  render() {
    return (
      <div style={{color: 'red', fontSize: '72px'}}>Big Red</div>
    );
  }
};
```

## Add Inline Styles in React

You may have noticed in the last challenge that there were several other syntax differences from HTML inline styles in addition to the style attribute set to a JavaScript object. 
- First, the names of certain CSS style properties use camel case.
For example, the last challenge set the size of the font with `fontSize` instead of `font-size`.
Hyphenated words like `font-size` are invalid syntax for JavaScript object properties, so React uses camel case.
As a rule, any hyphenated style properties are written using camel case in JSX.

All property value length units (like **height**, **width**, and **fontSize**) are assumed to be in **px** unless otherwise specified. 
If you want to use **em**, for example, you wrap the value and the units in **quotes**, like `{fontSize: "4em"}`. 
Other than the length values that default to **px**, all other property values should be wrapped in **quotes**.

```Javascript
const styles = {
  color: 'purple',
  fontSize: 40,
  border: '2px solid purple'
}

class Colorful extends React.Component {
  render() {
    return (
      <div style={styles}>Style Me!</div>
    );
  }
};
```

## Use Advanced JavaScript in React Render Method

In previous challenges, you learned how to inject JavaScript code into JSX code using curly braces, `{ }`, for tasks like accessing props, passing props, accessing state, inserting comments into your code, and most recently, styling your components. 
These are all common use cases to put JavaScript in JSX, but they aren't the only way that you can utilize JavaScript code in your React components.

You can also write JavaScript directly in your render methods, before the return statement, without inserting it inside of curly braces. 
This is because it is not yet within the JSX code. When you want to use a variable later in the JSX code inside the return statement, you place the variable name inside curly braces.

```Javascript
const inputStyle = {
  width: 235,
  margin: 5
};

class MagicEightBall extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInput: '',
      randomIndex: ''
    };
    this.ask = this.ask.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  ask() {
    if (this.state.userInput) {
      this.setState({
        randomIndex: Math.floor(Math.random() * 20),
        userInput: ''
      });
    }
  }

  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {
    const possibleAnswers = [
      'It is certain',
      'It is decidedly so',
      'Without a doubt',
      'Yes, definitely',
      'You may rely on it',
      'As I see it, yes',
      'Outlook good',
      'Yes',
      'Signs point to yes',
      'Reply hazy try again',
      'Ask again later',
      'Better not tell you now',
      'Cannot predict now',
      'Concentrate and ask again',
      "Don't count on it",
      'My reply is no',
      'My sources say no',
      'Most likely',
      'Outlook not so good',
      'Very doubtful'
    ];

    const answer = possibleAnswers[this.state.randomIndex];
    return (
      <div>
        <input
          type='text'
          value={this.state.userInput}
          onChange={this.handleChange}
          style={inputStyle}
        />
        <br />
        <button onClick={this.ask}>Ask the Magic Eight Ball!</button>
        <br />
        <h3>Answer:</h3>
        <p>
        {answer}
        </p>
      </div>
    );
  }
}
```

## Render with an If-Else Condition

Another application of using JavaScript to control your rendered view is to tie the elements that are rendered to a condition. 
When the condition is true, one view renders. 
When it's false, it's a different view. 
You can do this with a standard **if/else statement** in the `render()` method of a React component.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      display: true
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState((state) => ({
      display: !state.display
    }));
  }
  render() {
    if (this.state.display) {
      return (
         <div>
           <button onClick={this.toggleDisplay}>Toggle Display</button>
           <h1>Displayed!</h1>
         </div>
    );
    } else {
      return (
         <div>
           <button onClick={this.toggleDisplay}>Toggle Display</button>
         </div>
    );
    }
    
  }
};
```

## Use && for a More Concise Conditional

The if/else statements worked in the last challenge, but there's a more concise way to achieve the same result. 
Imagine that you are tracking several conditions in a component and you want different elements to render depending on each of these conditions. 
If you write a lot of else if statements to return slightly different UIs, you may repeat code which leaves room for error. 
Instead, you can use the `&&` logical operator to perform conditional logic in a more concise way. 
This is possible because you want to check if a condition is true, and if it is, return some markup. 

Here's an example:
```Javascript
{condition && <p>markup</p>}
```

- If the condition is true, the markup will be returned. 
- If the condition is false, the operation will immediately return false after evaluating the condition and return nothing.

You can include these statements directly in your JSX and string multiple conditions together by writing `&&` after each one. 
This allows you to handle more complex conditional logic in your `render()` method without repeating a lot of code.

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      display: true
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState(state => ({
      display: !state.display
    }));
  }
  render() {
    return (
       <div>
         <button onClick={this.toggleDisplay}>Toggle Display</button>
         {this.state.display && <h1>Displayed!</h1>}
       </div>
    );
  }
};
```

## Use a Ternary Expression for Conditional Rendering

**The ternary operator** is often utilized as a shortcut for if/else statements in JavaScript. 
They're not quite as robust as traditional if/else statements, but they are very popular among React developers. 
One reason for this is because of how JSX is compiled, **if/else statements can't be inserted directly into JSX code**. 

Ternary expressions can be an excellent alternative if you want to implement conditional logic within your JSX. 
Recall that a ternary operator has three parts, but you can combine several ternary expressions together. 
Here's the basic syntax:

```Javascript
condition ? expressionIfTrue : expressionIfFalse;
```

```Javascript
const inputStyle = {
  width: 235,
  margin: 5
};

class CheckUserAge extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      userAge: ''
    };
    this.submit = this.submit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }

  handleChange(e) {
    this.setState({
      input: e.target.value,
      userAge: ''
    });
  }

  submit() {
    this.setState(state => ({
      userAge: state.input
    }));
  }

  render() {
    const buttonOne = <button onClick={this.submit}>Submit</button>;
    const buttonTwo = <button>You May Enter</button>;
    const buttonThree = <button>You Shall Not Pass</button>;

    return (
      <div>
        <h3>Enter Your Age to Continue</h3>
        <input
          style={inputStyle}
          type='number'
          value={this.state.input}
          onChange={this.handleChange}
        />
        <br />
        {this.state.userAge === '' ? 
          buttonOne : 
          (parseInt(this.state.userAge, 10) < 18 ? buttonThree : buttonTwo)
        }
      </div>
    );
  }
}
```

## Render Conditionally from Props

So far, you've seen how to use `if/else`, `&&`, and the ternary operator `(condition ? expressionIfTrue : expressionIfFalse)` 
to make conditional decisions about what to render and when. 
However, there's one important topic left to discuss that lets you combine any or all of these concepts with another powerful React feature: `props`. 
Using `props` to conditionally render code is very common with React developers — 
that is, they use the value of a given prop to automatically make decisions about what to render.

```Javascript
class Results extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h1>{this.props.fiftyFifty ? "You Win!" : "You Lose!"}</h1>;
  }
}

class GameOfChance extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 1
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState(prevState => {
      return {
        counter: prevState.counter + 1
      }
    });
  }
  render() {
    const expression = Math.random() >= .5;
    return (
      <div>
        <button onClick={this.handleClick}>Play Again</button>
        {/* Change code below this line */}
        <Results fiftyFifty={expression} />
        {/* Change code above this line */}
        <p>{'Turn: ' + this.state.counter}</p>
      </div>
    );
  }
}
```

## Change Inline CSS Conditionally Based on Component State

Here's one more example that combines both of these topics. 
You can also render CSS conditionally based on the state of a React component. 
To do this, you check for a condition, and if that condition is met, 
you modify the styles object that's assigned to the JSX elements in the render method.

This paradigm is important to understand because it is a dramatic shift from the more traditional approach of applying styles by modifying DOM elements directly (which is very common with jQuery, for example). 
In that approach, you must keep track of when elements change and also handle the actual manipulation directly. 
It can become difficult to keep track of changes, potentially making your UI unpredictable. 
When you set a style object based on a condition, you describe how the UI should look as a function of the application's state. 
There is a clear flow of information that only moves in one direction. 
This is the preferred method when writing applications with React.

```Javascript
class GateKeeper extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({ input: event.target.value })
  }
  render() {
    let inputStyle = {
      border: '1px solid black'
    };
    inputStyle.border = this.state.input.length > 15 ? '3px solid red' : '1px solid black';
    return (
      <div>
        <h3>Don't Type Too Much:</h3>
        <input
          type="text"
          style={inputStyle}
          value={this.state.input}
          onChange={this.handleChange} />
      </div>
    );
  }
};
```

## Use Array.map() to Dynamically Render Elements

Conditional rendering is useful, but you may need your components to render an unknown number of elements. 
Often in reactive programming, a programmer has no way to know what the state of an application is until runtime, because so much depends on a user's interaction with that program. 
Programmers need to write their code to correctly handle that unknown state ahead of time. 
Using `Array.map()` in React illustrates this concept.

For example, you create a simple "To Do List" app. 
As the programmer, you have no way of knowing how many items a user might have on their list. 
You need to set up your component to dynamically render the correct number of list elements long before someone using the program decides that today is laundry day.

```Javascript
const textAreaStyles = {
  width: 235,
  margin: 5
};

class MyToDoList extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInput: '',
      toDoList: []
    }
    this.handleSubmit = this.handleSubmit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleSubmit() {
    const itemsArray = this.state.userInput.split(',');
    this.setState({
      toDoList: itemsArray
    });
  }
  handleChange(e) {
    this.setState({
      userInput: e.target.value
    });
  }
  render() {
    const items = this.state.toDoList.map(elem => <li>{elem}</li>);
    return (
      <div>
        <textarea
          onChange={this.handleChange}
          value={this.state.userInput}
          style={textAreaStyles}
          placeholder='Separate Items With Commas'
        />
        <br />
        <button onClick={this.handleSubmit}>Create List</button>
        <h1>My "To Do" List:</h1>
        <ul>{items}</ul>
      </div>
    );
  }
}
```

## Give Sibling Elements a Unique Key Attribute

The last challenge showed how the map method is used to dynamically render a number of elements based on user input. 
However, there was an important piece missing from that example. 
When you create an array of elements, each one needs a key attribute set to a unique value. 
React uses these keys to keep track of which items are added, changed, or removed. 
This helps make the re-rendering process more efficient when the list is modified in any way.

Note: Keys only need to be unique between sibling elements, they don't need to be globally unique in your application.

```Javascript
const frontEndFrameworks = [
  'React',
  'Angular',
  'Ember',
  'Knockout',
  'Backbone',
  'Vue'
];

function Frameworks() {
  const renderFrameworks = frontEndFrameworks.map(elem => <li key={elem}>{elem}</li>);
  return (
    <div>
      <h1>Popular Front End JavaScript Frameworks</h1>
      <ul>
        {renderFrameworks}
      </ul>
    </div>
  );
};
```

## Use Array.filter() to Dynamically Filter an Array

The `map` array method is a powerful tool that you will use often when working with React. 
Another method related to `map` is `filter`, which filters the contents of an array based on a condition, then returns a new array. 
For example, if you have an array of users that all have a property online which can be set to true or false, you can filter only those users that are online by writing:
```Javascript
let onlineUsers = users.filter(user => user.online);
```

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      users: [
        {
          username: 'Jeff',
          online: true
        },
        {
          username: 'Alan',
          online: false
        },
        {
          username: 'Mary',
          online: true
        },
        {
          username: 'Jim',
          online: false
        },
        {
          username: 'Sara',
          online: true
        },
        {
          username: 'Laura',
          online: true
        }
      ]
    };
  }
  render() {
    const usersOnline = this.state.users.filter(elem => elem.online); 
    const renderOnline = usersOnline.map((user) => <li key={user.username}>{user.username}</li>); 
    return (
      <div>
        <h1>Current Online Users:</h1>
        <ul>{renderOnline}</ul>
      </div>
    );
  }
}
```

## Render React on the Server with renderToString

So far, you have been rendering React components on the client. 
Normally, this is what you will always do. 
However, there are some use cases where it makes sense to render a React component on the server. 
Since React is a JavaScript view library and you can run JavaScript on the server with Node, this is possible. 
In fact, React provides a `renderToString()` method you can use for this purpose.

There are two key reasons why rendering on the server may be used in a real world app. 
- First, without doing this, your React apps would consist of a relatively empty HTML file and a large bundle of JavaScript when it's initially loaded to the browser. 
This may not be ideal for search engines that are trying to index the content of your pages so people can find you. 
If you render the initial HTML markup on the server and send this to the client, the initial page load contains all of the page's markup which can be crawled by search engines. 
- Second, this creates a faster initial page load experience because the rendered HTML is smaller than the JavaScript code of the entire app. 
React will still be able to recognize your app and manage it after the initial load.

```Javascript
class App extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <div/>
  }
};

ReactDOMServer.renderToString(<App />);
```
