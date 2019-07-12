# React-Redux-Notes

___

## Redux

### Redux Basics

* `store` - An application will create a single Redux `store` to hold all data and state. We can view the state of the store by calling `store.getState()`. 

  The store's state should never be modified directly; instead, we call `store.dispatch(action)` to dispatch actions into the store.

* `action` - `action`(s) should be plain objects containing a `type` field, e.g. `{type: 'INCREMENT'}`. 

  You can define any types you want. You may also include other fields in the `action` object. 
  
  By convention, we often pass extra data in a `payload` field, e.g. `{type: 'SET_VALUE', payload: 42}`.

* `reducer` - You then define a function to handle `action`(s), and update the store accordingly. 

  You can choose how to update the state depending on which `type` of action your `reducer` function receives. 
  
  Redux will pass this function the current state of the `store`, and the `action` you dispatched, expecting an updated state object to be returned: `(state, action) => newState`. We call this function a `reducer` function.
  
* `Provider` - React Redux exposes the `Provider` component to handle passing our store to every container component. We'll generally use this to wrap the root component of our app, e.g. `<Provider store={store}> ... </Provider>`.

* `connect(mapStateToProps)(Component) => Component` - We use `connect()` to access the state of our `store` in our container components.

  Call `connect(mapStateToProps)` with a function that takes the state of the store, mapping it to props to be passed into our container component, `(state) => props`. 

  Calling `connect()` returns another function, which we should then call with our container component, `connect(...)(Component)`, to get a "connected" component. This connected component will automatically have a `dispatch` prop (for dispatching actions), and the result of `mapStateToProps` will be merged into the component's props.

  
* In a React Redux app, you create a single Redux `store` that manages the `state` of your entire app. Your React components `subscribe` to only the pieces of data in the `store` that are relevant to their role. Then, you `dispatch` the `actions` directly from React components, which then trigger `store` updates.

___

### Redux: Create a Redux Store

* The Redux store is the single source of truth when it comes to application state.

* The Redux `store` is an object which holds and manages application state. 

  There is a method called `createStore()` on the Redux object, which you use to create the Redux `store`. 
  
  This method takes a `reducer` function as a required argument. It simply takes `state` as an argument and returns `state`.


### Redux: Get State from the Redux Store

* The Redux `store` object provides several methods that allow you to interact with it. 

  For example, you can retrieve the current `state` held in the Redux `store` object with the `getState()` method.
  

### Redux: Define a Redux Action

* In Redux, all state updates are triggered by dispatching actions. An `action` is simply a JavaScript object that contains information about an action event that has occurred. 

  The Redux `store` receives these `action` objects, then updates its `state` accordingly. Sometimes a Redux `action` also carries some data. 
  
  While the data is optional, actions must carry a `type` property that specifies the 'type' of action that occurred.
  

### Redux: Define an Action Creator

* After creating an `action`, the next step is sending the `action` to the Redux `store` so it can update its `state`. 

  In Redux, we do this with an action creator (A JavaScript function that returns an `action`).
  
  In other words, action creators create objects that represent action events.


### Redux: Dispatch an Action Event

* Calling the `dispatch()` method, passing it the value returned from an action creator, sends an `action` back to the `store`.


### Redux: Handle an Action in the Store

* Reducers in Redux are responsible for the state modifications that take place in response to actions. 

* A `reducer` takes `state` and `action` as arguments, and it always returns a new `state`.

* The `reducer` is simply a pure function that takes `state` and `action`, then returns new `state`.

* In Redux, `state` is read-only. In other words, the `reducer` function must always return a new copy of `state` and never modify `state` directly.


### Redux: Use a Switch Statement to Handle Multiple Actions

* 

### Redux: Use const for Action Types

*


### Redux: Register a Store Listener With store.subscribe()

* The Redux `store` method `store.subscribe()` allows you to subscribe listener functions to the `store`, which are called whenever an `action` is dispatched against the `store`. 

  One simple use for this method is to subscribe a function to your `store` that simply logs a message every time an `action` is received and the `store` is updated.


### Redux: Combine Multiple Reducers

* Redux provides `reducer` composition as a solution for a complex `state` model. You define multiple reducers to handle different pieces of your application's `state`, then compose these reducers together into one root `reducer`. 

  The root `reducer` is then passed into the Redux `createStore()` method.
  
*  Redux provides the `combineReducers()` method, it accepts an object as an argument in which you define properties which associate keys to specific reducer functions. 

  The name you give to the keys will be used by Redux as the name for the associated piece of `state`.

  ```js
  const rootReducer = Redux.combineReducers({
    auth: authenticationReducer,
    notes: notesReducer
  });
  ```
    
   The `auth` and `notes` keys will each hold the `state` associated with it and handled by the `authenticationReducer` and `notesReducer` reducers respectively.

### Redux: Send Action Data to the Store

* 

### Redux: Use Middleware to Handle Asynchronous Actions

* Redux provides middleware designed specifically for asynchronous requests, called Redux Thunk middleware. 

* To include Redux Thunk middleware, you pass it as an argument to `Redux.applyMiddleware()`. This statement is then provided as a second optional parameter to the `createStore()` function.


### Redux: Never Mutate State

* Immutable state means that you never modify state directly, instead, you return a new copy of state.

   This immutability, in fact, is what provides such features as time-travel debugging that you may have heard about.
   
* Redux does not actively enforce state immutability in its store or reducers, that responsibility falls on the programmer.

### Use the Spread Operator on Arrays

* One solution from ES6 to help enforce state immutability in Redux is the spread operator: `...`. 

  The spread operator has a variety of applications, one of which is well-suited to the previous challenge of producing a new array from an existing array. 
  
* The `...` effectively spreads out the values in an array into a new array, this is great for cloning arrays.

  But it's important to note that it only makes a shallow copy of the array. That is to say, it only provides immutable array operations for one-dimensional arrays.
___

### Remove an Item from an Array

* Removing items from an array without mutating `state` requires usage of the spread operator, `...`, as well as the `slice()` and `concat()` array methods.
___

### Copy an Object with Object.assign

* `Object.assign()` takes a target object and source objects and maps properties from the source objects to the target object. 

  Any matching properties are overwritten by properties in the source objects. This behavior is commonly used to make shallow copies of objects by passing an empty object as the first argument followed by the object(s) you want to copy. 
  
  Here's an example:
  ```js
  const newObject = Object.assign({}, obj1, obj2);
  ```
  This creates `newObject` as a new `object`, which contains the properties that currently exist in `obj1` and `obj2`. 
  
  It does so by mapping the properties from `obj2` onto `obj1` first, and then mapping the properties from `obj1` onto the empty object argument, `{}`.

___

___

## React Redux

### Getting Started with React Redux

* Because Redux is not designed to work with React out of the box, you need to use the `react-redux` package. It provides a way for you to pass Redux `state` and `dispatch` to your React components as `props`.

___

### Use Provider to Connect Redux to React

* React Redux provides a small API with two key features: `Provider` and `connect`. 

  The `Provider` is a wrapper component from React Redux that wraps your React app. 
  
  This wrapper then allows you to access the Redux `store` and `dispatch` functions throughout your component tree. 
  
  `Provider` takes two props: The Redux store and the child components of your app. 
  
  Defining the `Provider` for an App component might look like this:
  ```js
  <Provider store={store}>
    <App/>
  </Provider>
  ```
___

### Map State to Props

*  The `Provider` component allows you to provide `state` and `dispatch` to your React components, but you must specify exactly what state and actions you want. This way, you make sure that each component only has access to the state it needs. 

  You accomplish this by creating two functions: `mapStateToProps()` and `mapDispatchToProps()`.
  
* In these functions, you declare what pieces of state you want to have access to and which action creators you need to be able to dispatch. 

_Note_: Behind the scenes, React Redux uses the `store.subscribe()` method to implement `mapStateToProps()`.

___

### Map Dispatch to Props

* The `mapDispatchToProps()` function is used to provide specific action creators to your React components so they can dispatch actions against the Redux store. 

It returns an object that maps dispatch actions to property names, which become component `props`. However, instead of returning a piece of `state`, each property returns a function that calls `dispatch` with an action creator and any relevant action data. 

You have access to this `dispatch` because it's passed in to `mapDispatchToProps()` as a parameter when you define the function, just like you passed state to `mapStateToProps()`.

_Note_: Behind the scenes, React Redux is using Redux's `store.dispatch()` to conduct these dispatches with `mapDispatchToProps()`.

___

### Connect Redux to React

* 







