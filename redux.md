# Notes from Egghead [Getting Started With Redux](https://egghead.io/lessons/javascript-redux-the-single-immutable-state-tree?series=getting-started-with-redux)

### Storing state
- Represent state of app as a single js object
- Every change to the app (data, ui state) results in a change to the object / state-tree

### Changing state
- Dispatch an action object describing the change
- Must have a type that is not undefined (recommend strings)
- Ex. counter has types "INCREMENT" and "DECREMENT"

* Pure functions 
- do not change or modify arguments
- generate result solely using the passed arguments
- product the same result every time

### Describing state mutations
- The reducer
- View layer as a pure function
- accept previous state and the action, return the next state

[Basic reducer](https://gist.github.com/anonymous/31af2be2f5abe65e44c5)
```javascript
function counter(state = 0, action) {
  if (action.type === 'INCREMENT') {
    return state + 1;
  } else if (action.type === 'DECREMENT' ){
    return state - 1;
  }
  return state;
}

expect(
  counter(0, {type: 'INCREMENT'})
).toEqual(1);

expect(
  counter(1, {type: 'INCREMENT'})
).toEqual(2);

expect(
  counter(2, {type: 'DECREMENT'})
).toEqual(1);

expect(
  counter(1, {type: 'DECREMENT'})
).toEqual(0);

expect(
  counter(1, {type: 'SOMETHING_ELSE'})
).toEqual(1);

expect(
  counter(undefined, {})
).toEqual(0);

console.log('Tests passed!');
```
