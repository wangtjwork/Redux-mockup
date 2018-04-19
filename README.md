# Self-Written Redux

## Description

Write Redux's key features following [Udacity's React Nanodegree]{https://www.udacity.com/course/react-nanodegree--nd019}.

Redux is a JS library for __predictive__ state management, could be combined with any UI framework/library and even just vanilla JavaScript.

It has to have four key abilities:
1. Store state.
2. Get current state.
3. Listen to state changes.
4. Update state.

In this project, we'll first write some JS functions ourselves that has these abilities. Then, we'll add some UI to the page to see that we are actually managing all the states with ease.

*By accident*, our API is just the same as Redux's! So we can switch to Redux API, and see how Redux manages Vanilla JavaScript.

Next, we'll add React instead of our own UI rendering, and see how the two couples together.

## How Redux Works
Redux solves the key abilities by providing a store that:
1. stores state, created by API createStore().
2. provides an API getState() to get current state.
3. provides an API subscribe() to execute functions when state changes.
4. provides an API dispatch() to take in actions, and invoke [reducers](#reducer), passing the action.

### Reducer:
A Reducer must be a [pure function](]{https://en.wikipedia.org/wiki/Pure_function), making sure the state changes are __predictable__. Reducers are added to the Redux store at create time.

Reducers update state according to the actions passed in by dispatch(). In order to better organize actions (and of course, DRY), they are often the return value of __ActionCreators__.

### Middleware:
Sometimes, we would like some moves to be taken *before* the action causes the reducer to run. Typical use cases include filter on action or logger.

We can certainly make our own by wrapping the dispatch function. However, it's already provided in Redux, we can pass an optimal middleware parameter to create the store.

## Third-party libraries

### React
Redux could work with vanilla JS, but it would be a lot easier to work with auto UI rendering library: React.

With React taking care of UI rendering, we can picture Redux as pure state, and React as a result from the state.

### Redux Thunk
To work with asynchronous data, we can load them in componentDidMount lifecycle hook, quite like what a normal React component would do, only difference is to invoke store.dispatch instead of storing data directly inside component.

However, that adds complexity to our component, and we may want to have *separate of concerns*. Therefore, the ideal place for requests would be to move the asynchronous logic into ActionCreators.

Right now, ActionCreators can only return objects. We can write our own logic inside them to handle Promises and resolve into objects, but luckily we already have a __Redux Thunk__ library to handle that for us. It kind of wraps the dispatch() function, taking in objects, functions or promises and calls the real dispatch() function when appropriate.

### React-Redux
Each component in React would have to have access to the store in order to know the state. This becomes a problem in large apps with many nested layers and components. It's quite a bad idea to pass the store 10 layers down just so the component can access a slice of it.

React-Redux uses [React Context](https://reactjs.org/docs/context.html) to make the store available to all the child components. It also provides a wrapper for components, in order for them to be passed in a slice of the state.
