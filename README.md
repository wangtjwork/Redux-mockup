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
1. stores state
2. provides an API getState() to get current state.
3. provides an API subscribe() to execute functions when state changes.
4. takes in [reducers](#reducer) to update states.

### Reducer:
A Reducer must be a [pure function](]{https://en.wikipedia.org/wiki/Pure_function), making sure the state changes are __predictable__.

Reducers takes in __actions__ to decide how to update a state.
