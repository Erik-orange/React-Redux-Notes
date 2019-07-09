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
