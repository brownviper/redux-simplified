[application state management with Redux](https://redux.js.org/api/store) explained in a very simple way.

a lot of confusion happen when developers try to explain redux usage to their peers.
Majority of people try and learn/teach Redux using other frameworks, i.e [ReactJS](https://reactjs.org/).

Beside the burden to understand reactJs moving parts like state, props, components, JSX, ... etc.
we accidentally add the state management to the mix.

so here, you will get none of that. here we only talk Redux.
once you understand the basic principle, then applying it in any framework, 
whether that is Angular, React, Vue or any other, guess what "it does not matter".

I can simplify the state management with Redux store in a nn - steps.

- you need to import redux. in our index.html file, we add `https://unpkg.com/redux@latest/dist/redux.js` 
- create the action function, returning an object, with the mandatory type field defined.

```
    function pushAction(value) {
        return {
            type: 'PUSH',
            number: value
        };
    }
```

- create the reducer function, that knows how to deal with the action

```
    function pushReducer(state, action) {
        // initialise the state if its undefined
        if(state === undefined) {
            state = [];
        }
        
        // check for the action the reducer care about
        if(action.type === 'PUSH') {
            state.concat(action.number);
        }
    
        // now we can return the new state
        return state;
    }
``` 

- now to create the store by telling Redux createStore about our reducer.

```
    var store = Redux.createStore(pushReducer); 
```

- now if you ask the store about its state, it should tell us its state is empty

```
    console.log(store.state);
```

- the state should be an empty array []

- the store was told about the reducer, now to link the action, `disptach` function comes into play

```
    store.dipatch(pushAction(4));
    store.dipatch(pushAction(5));
```
- now check the new state

```
    console.log(store.state);
```

and we should see [4,5]