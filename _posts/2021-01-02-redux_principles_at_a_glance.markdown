---
layout: post
title:      "Redux Principles at a Glance"
date:       2021-01-03 00:21:14 +0000
permalink:  redux_principles_at_a_glance
---


During the last module in Bootcamp, I was finally starting to wrap my head around React when we started learning Redux.  When it comes to managing state while building complex tasks, you'll want to use Redux.  It is a pattern for managing state so when you have reasonable amounts of data changing over time, Redux will come in handy.  Sometimes an application can become so complex that you are confused about where state is stored or how state changes, this is where the benefits of Redux come into play.  

Redux is generally explained using three fundamental principles.  Below is a short review of Redux principles along with its core concepts that will help to outline what it's all about:

**Single source of truth**:  this essentially means that there is only one place that represents the state of the application.  The *global state* of your app is stored in an object tree within a single *store*.  With this there are two concepts to understand:
* State - specifically in Redux it refers to the single state value, controlled by the store and returned by getState().  It holds the entire state of a Redux application.  
* Store - this is an object that holds the application's state tree.  There is only a single store in Redux.


**State is read only**:  The only way to change the state is to provide an *action* or an object explaining what should happen.  These actions express an intent to transform the state rather than writing directly to the state.  When declared this is what's called "dispatching an action".  
* Action - These are the only sources of information for the store.  They are objects that hold whatever intention you want performed on the state.  Actions must have a type field to indicate the type of action being performed.  

```
export const getBooks = () => {
    return (dispatch) => {
        fetch(`http://localhost:3001/books`)
            .then((res) => res.json())
            .then((books) => 
                dispatch({ type: 'FETCH_BOOKS_SUCCESS', payload: books })
        );
    };
};

export const createBook = (data) => {
    return (dispatch) => {
        fetch(`http://localhost:3001/books`, {
            method: "POST", 
            headers: {
            'Content-Type': 'application/json',
        },
            body: JSON.stringify({ book: data }),
        })
            .then((res) => res.json())
            .then((book) => 
                dispatch({ type: 'CREATE_BOOK_SUCCESS', payload: book })
            );
    }
}
```


**Changes are made with pure functions**:  In order to identify how the state is modified by actions, pure *reducers* are needed.  Reducers can be simple functions that receive the current state and an action, and returns the current state or new state.  These will never alter or modify global objects.
* Reducer -  a function that accepts an accumulation and a value and returns a new accumulation. They are used to reduce a collection of values down to a single value.

```
function bookReducer(state = { all: [] }, action) {
    switch(action.type) {
        case "FETCH_BOOKS_SUCCESS":
            return { ...state, all: action.payload };

        case "CREATE_BOOK_SUCCESS":
            return { ...state, all: [...state.all, action.payload] }
```

To recap, the basic flow of Redux goes like this: a component dispatches an action, the reaction is reduced based on its type and may result in a new state. If so, the new state is sent to the store who then notifies all components that need to know about the change, potentially causing them to re-render.

![](https://i2.wp.com/cdn-images-1.medium.com/max/1600/0*igA-RO7ila55cVWb.png?ssl=1)

[https://stackoverflow.com/questions/45416237/axios-calls-in-actions-redux](https://stackoverflow.com/questions/45416237/axios-calls-in-actions-redux)

There are more advanced principles within Redux however as a new programmer who is just diving in, understanding these core concepts provide a solid baseline to begin your Redux journey.  
