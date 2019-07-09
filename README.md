# React-Redux-Notes

___

## Redux: Create a Redux Store

* The Redux store is the single source of truth when it comes to application state.

* The Redux `store` is an object which holds and manages application state. 

  There is a method called `createStore()` on the Redux object, which you use to create the Redux `store`. 
  
  This method takes a `reducer` function as a required argument. It simply takes `state` as an argument and returns `state`.


## Redux: Get State from the Redux Store

* The Redux `store` object provides several methods that allow you to interact with it. 

  For example, you can retrieve the current `state` held in the Redux `store` object with the `getState()` method.
  

## Redux: Define a Redux Action

* In Redux, all state updates are triggered by dispatching actions. An `action` is simply a JavaScript object that contains information about an action event that has occurred. 

  The Redux `store` receives these `action` objects, then updates its `state` accordingly. Sometimes a Redux `action` also carries some data. 
  
  While the data is optional, actions must carry a `type` property that specifies the 'type' of action that occurred.
  

## Redux: Define an Action Creator

* After creating an `action`, the next step is sending the `action` to the Redux `store` so it can update its `state`. 

  In Redux, we do this with an action creator (A JavaScript function that returns an `action`).
  
  In other words, action creators create objects that represent action events.


## Redux: Dispatch an Action Event

* Calling the `dispatch()` method, passing it the value returned from an action creator, sends an `action` back to the `store`.


## Redux: Handle an Action in the Store

* Reducers in Redux are responsible for the state modifications that take place in response to actions. 

* A `reducer` takes `state` and `action` as arguments, and it always returns a new `state`.

* The `reducer` is simply a pure function that takes `state` and `action`, then returns new `state`.

* In Redux, `state` is read-only. In other words, the `reducer` function must always return a new copy of `state` and never modify `state` directly.


## Redux: Use a Switch Statement to Handle Multiple Actions

* 

## Redux: Use const for Action Types

*


## Redux: Register a Store Listener With store.subscribe()

* The Redux `store` method `store.subscribe()` allows you to subscribe listener functions to the `store`, which are called whenever an `action` is dispatched against the `store`. 

  One simple use for this method is to subscribe a function to your `store` that simply logs a message every time an `action` is received and the `store` is updated.


## Redux: Combine Multiple Reducers

* Redux provides reducer composition as a solution for a complex state model. You define multiple reducers to handle different pieces of your application's `state`, then compose these reducers together into one root reducer. 

  The root `reducer` is then passed into the Redux `createStore()` method.
  
*  Redux provides the `combineReducers()` method, it accepts an object as an argument in which you define properties which associate keys to specific reducer functions. 

  The name you give to the keys will be used by Redux as the name for the associated piece of `state`.

  ```js
  const rootReducer = Redux.combineReducers({
    auth: authenticationReducer,
    notes: notesReducer
  });
```

## Redux: Send Action Data to the Store

* 












