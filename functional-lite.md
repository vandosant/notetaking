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

var z = multiply(3,4);
z = sum(z,5) // 17
