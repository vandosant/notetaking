### Notes From Frontend Masters [ES6](https://frontendmasters.com/courses/jsnext-es6/)

### History
- [Harmony](http://wiki.ecmascript.org/doku.php?id=harmony:harmony)
- [ES Discuss](https://esdiscuss.org/)
- [Compat-Table](https://kangax.github.io/compat-table/es6/)

### Repl
[Babel repl](https://babeljs.io/repl/)

### Tail calls
- [Babeldocs#tail-calls](https://babeljs.io/docs/learn-es2015/#tail-calls)
- Calls in tail-position do not grow the stack infinitely.

### Rest Params
- `function yello(...bar){ console.log(bar); console.log(typeof(bar) === 'array')};`
- 1 per function
- Must be last param
- Can't use default arguments anymore
- Cannot give rest param a default value

### Spread
- `...` before an array
- `var a = [1,2,3];`
- `console.log(...a); // 1 2 3`

### Destructuring
- With objects
- `let {name, email} = getUser();`
- `console.log(name, email);`
- `let {name: n, email: e} = getUser();`
- `console.log(n, e);`
- With functions
- `var user = {name: 'x', email: 'y'}; displayUser(user);`
- `function displayUser({name, email}){};`
- `function displayUser({name = "None provided", email = "None provided"}){};`
- With arrays
- `var nums = [1,2,3,4,5,6,7,8,9,10];`
- `var [first, second,,,fifth] = nums;`
- `console.log(first, second, fifth);`
