Notes from [Functional lite js](https://frontendmasters.com/courses/functional-js-lite/#v=mpx9vosfmi)

### Side effects
- Identify stateful variables
- Identify mutated variables
- Identify required input and output
- Wrap mutating operations in a closure and pass in the required universe
- Perform required operation(s)
- Encapsulate and return observed end state
- From the outside, now the operation is pure (can call with same input and get same output)

### Composition
- Functions calling and returning other functions
```javascript
function sum(x,y) { return x + y };
function multiply(x,y) { return x * y };

// stateful method
var z = multiply(3,4);
z = sum(z,5);
z; // 17

// pure method
sum(multiply(3,4),5); // 17

// manual composition
function multAndSum(x,y,z) {
  return sum( multiply(x,y), z);
};
multAndSum(3,4,5); // 17
```

### Closure
- When a function "remembers" variables within its scope and can reference them after being invoked
- AKA Currying and partial application
```javascript
function foo(x,y) {
  return function() {
    return x + y;
  }
}

var x = foo(3,4);

x();	// 7
x();	// 7
```

### Recursion
- A function that calls itself until a base case is reached
- Assumes unlimited CPU and memory
- Each recursive call invokes another stackframe, which is thrown away when the call finishes
- Modern browsers have limits of 10-20K stackframes allocated
- Tail-call optimization: If function call is last and returns the result, current stackframe can be discarded
```javascript
function mult(...args) {
	if (args.length <= 2) {
		return args[0] * args[1]
	}
	return args[0] * mult(...args.slice(1))
}

mult(3,4,5);	// 60

mult(3,4,5,6);	// Oops!
```
