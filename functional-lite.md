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

### List Operations
- Transformation (map): returns 1:1 mapping of the list with the transform applied to each element
- Exclusion (filter): Predicate returns true to keep, false to discard
- Composition (reduce): Fully or partially apply an operation to a list and value (accumulator) and return the output as applied to the value
  - Partial application: Uniques -- initial accumulator of an empty list[] that collects unique list values
- Iteration (forEach): Useful when you intend to produce some side effects, such as logging values

### Exercise

- Create a function that accepts an arbitrary list of values and adds them up  

######With a for-loop
```javascript
// functions as args
function foo(x) {
  return function() {
    return x
  };
}

function add(x, y) {
  return x + y;
}

function add2(f1, f2) {
  return add(f1(),f2());
}

function addN(args) {
  var result = 0;
  for (var i = 0; i < args.length; i++) {
    result = add2(foo(result),args[i])
  }
  return result
}

console.log(addN([foo(42), foo(10)]));
```
```javascript
// values as args
function foo(x) {
  return function() {
    return x
  };
}

function add(x, y) {
  return x + y;
}

function add2(f1, f2) {
  return add(f1(),f2());
}

function addN(args) {
  var result = 0;
  for (var i = 0; i < args.length; i++) {
    result = add2(foo(result), foo(args[i]))
  }
  return result
}

console.log(addN([42,11,88]));
```
######With Recursion
```javascript
// recursively
function foo(x) {
  return function() {
    return x
  };
}

function add(x, y) {
  return x + y;
}

function add2(f1, f2) {
  return add(f1(),f2());
}

function addN(args) {
  if (args.length === 2) {
    return add2(foo(args[0]), foo(args[1]))
  }

  return args[0] + addN(args.slice(1));
}

console.log(addN([42,12,88]));
```
```javascript
// recursively (tail call optimized)
function foo(x) {
  return function () {
    return x
  };
}

function add(x, y) {
  return x + y;
}

function add2(f1, f2) {
  return add(f1(), f2());
}

function addN(args) {
  if (args.length == 2) {
    return add2(foo(args[0]), foo(args[1]))
  }
  return addN([add2(foo(args[0]), foo(args[1]))].concat(args.slice(2)))
}

console.log(addN([42, 12, 88, 99]));
```
######With List Operations
```javascript
// with map & reduce
function foo(x) {
  return function () {
    return x
  };
}

function add(x, y) {
  return x + y;
}

function add2(f1, f2) {
  return add(f1(), f2());
}

function addN(args) {
  var foos = args.map(foo);
  return foos.slice(1).reduce(function (acc, next) {
    return function () {
      return add2(acc, next)
    }
  }, foos[0])()
}

console.log(addN([42, 12, 88]));
```
```javascript
// with a filter
function foo(x) {
  return function () {
    return x
  };
}

function add(x, y) {
  return x + y;
}

function add2(f1, f2) {
  return add(f1(), f2());
}

function addN(args) {
  return args.slice(1).reduce(function (acc, next) {
    return function () {
      return add2(acc, next)
    }
  }, args[0])()
}

function isOdd(x) {
  return x % 2 == 1;
}
function isEven(x) {
  return composeNeg(isOdd(x));
}
function composeNeg(x) {
  return !x
}

console.log(addN([2, 3, 6, 7].filter(isEven).map(foo)));
```
