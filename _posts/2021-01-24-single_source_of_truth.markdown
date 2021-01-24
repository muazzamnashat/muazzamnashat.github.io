---
layout: post
title:      "Single Source of truth"
date:       2021-01-24 07:37:44 -0500
permalink:  single_source_of_truth
---


If you know the basics of React, then you are most probably familiar with the keyword PROPS! React is a component-based library which means that it splits the UI into different components and all the components together build the UI. For the components to work together they need to communicate with each other and ensure the data consistency throughout the application. Props is the way the components communicate. But this props can flow in one-way, from parent component to child components. While this unidirectional data flow helps maintain a clean data flow architecture, this can get massy as the application grows. When there are several components sharing data with each other, it may become hard to pass props to several components and keep track of our props as it gets bigger.

This is where *Redux* shines! It encourages a single source of truth by storing all the data in a single JavaScript object separated from all the components. And the best part is we can access the data from any component anytime just by connecting the component to the object which is called redux store! 

Today, I'll walk you through on how to setup a Redux store in a React app. I'll assume you have already spinned up a react app with create-react-app. 


*  First we need to import ‘’createStore” method from the Redux library.  Before that we can need to install two packages `redux` and `react-redux` by running 
`npm install redux && npm install react-redux`
After the installation we can import createStore method from redux by

```
// ./src/index.js
import { createStore } from 'redux';
```

Now we can create our Redux store by running this createStore method.

```
// ./src/index.js

const store = createStore(countReducer);
```

We’ll get back to the countReducer in a bit. 

* 	Now we need the store to be available to the whole application. To do that, we’ll need to import Provider component from `react-redux` and the Provider component will wrap our top-level component which is usually App.js. Then, the App or any components inside App will have access to the Redux store.

```
// ./src/index.js
import {Provider} from 'react-redux';
```

And then this is how we wrap our App component within Provider component.

```
<Provider store={store}>
    <App />
  </Provider>
```

These steps will be done inside our src/index.js . 

* 	Now, to change the data in our store, we’ll need reducers. Reducers are simple JS functions that have a type and a payload. Type usually means the type of action we want to take, i.e., how we want to change our store. This can be “INCREASE_COUNT’’ which may mean that we are increasing the count in our redux store. Assuming the redux store has a count key.   And, the payload is the data that we want to add, delete or replace with in our store. A simple reducer can be like this.

```
// ./src/reducers/counterReducer.js
 
export default function counterReducer (
  state = {
    count: 0
  },
  action
) {
  switch (action.type) {
    case 'INCREASE_COUNT':
      return {
        ...state,
        count: state.count + 1 
      }
    default:
      return state;
  }
}
```

Here when we pass an action with type 'INCREASE_COUNT', it will increase the count by 1 in our store. 

* 	Now to change the data or access the data in our store, we’ll need to import connect provided by react-redux.

```
// ./src/App.js
import { connect } from 'react-redux';
```

Now we can modify a component’s export method and include connect to gain access to the store and dispatch method. Dispatch method takes in an action.

```
// ./src/App.js

const mapStateToProps = state => {
  return {
    count: state.count
  };
};
 
const mapDispatchToProps = dispatch => {
  return {
    increaseCount: () => dispatch({ type: 'INCREASE_COUNT' })
  };
};
 
export default connect(
  mapStateToProps,
  mapDispatchToProps
)(App);
```

Here with the mapStateToProps function, we are mapping the store data to the components props which can be accessed as this.props.count . And, with mapDispatchToProps , we are mapping the dispatch to the props, which can be invoked with this.props.increaseCount() and it will increase the count in our redux store.

After the set-up, our component will look like this:

```
// ./src/App.js
 
import React, { Component } from 'react';
import { connect } from 'react-redux';
import './App.css';
 
........
 
const mapStateToProps = state => {
  return {
    items: state.items
  };
};
 
const mapDispatchToProps = dispatch => {
  return {
    increaseCount: () => dispatch({ type: 'INCREASE_COUNT' })
  };
};
 
export default connect(
  mapStateToProps,
  mapDispatchToProps
)(App);
```


```
// ./src/index.js
 
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore } from 'redux';
import { Provider } from 'react-redux';
import countReducer from './reducers/countReducer';
import App from './App';
import './index.css';
 
const store = createStore(countReducer)
 
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```


Now, we may have a button in our App component that will trigger the dipatch method and increase count in the redux store and a div to show the current count. This is a very high-level walkthrough on how to set-up a redux store in a React app. This may seem unnecessary to have all these setup just to keep track of a count when we can do that in out component state but as the app grows bigger with complex logic and data, a single souce of truth will be really helpful. 
 

