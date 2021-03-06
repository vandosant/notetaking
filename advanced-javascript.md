### Notes From Frontend Masters [Advanced JavaScript](https://frontendmasters.com/courses/advanced-javascript/)

### Resources
[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)  
[Style Guide](https://github.com/rwaldron/idiomatic.js/)  
[Spec](http://www.ecma-international.org/publications/standards/Ecma-262.htm)  
[Spec Proposals](http://wiki.ecmascript.org/doku.php?id=harmony:proposals)  

- Function declarations start with the function keyword
- else it is a function expression, eg `var foo = function bar() {}`
- Function expression variable declarations are enclosed in their own scope
- Anonymous function expression negatives
    1. No ability to self-reference
    2. Nothing to reference in debugging
    3. Less self-documentation

### Scope
- Lexical scoping by default
- `catch` / `try` is block scoped
- `eval` modifies existing lexical scope
- `with` creates a lexical scope at runtime
- `let` creates block scope `for (let i = 0; i < bar.length; i++)`

### Hoisting
- Variable declarations are moved to the top
- In reality variables are being declared at compilation
- Functions are hoisted above variables

### `this`
Only the call site matters

1. Default binding
  - Normal function call / IIFE `foo()`
2. Implicit binding
  - Object property reference `o2.foo()`
3. Explicit binding
  - Call or apply utility functions `foo.call(o3)`
  - Hard binding
    - `function foo() { console.log(this.bar); };`
    - `var orig = foo;`
    - `foo = function() { orig.call(obj); };`
    - AKA `bind` utility from ES5
4. `new` constructor binding
  - Modification to the way function is being called `new foo()`
  1. New object is created*
  2. Created object is linked to a different object
  3. Created object is bound as `this` for function
  4. Implicitly insert `return this` if there is not a return value

1. Is there a `new` keyword?
2. Is call or apply used (also bind)
3. Is there an owning or containing object?
4. Default binding

### Closure
- Ability of a function to access lexical scope even when it is executed outside of that scope
- Module pattern works well for this -- A function when executed returns another function or group of functions that encapsulate the parent lexical scope.

### Delegation
- Live linkage at runtime between objects

### Prototype Delegation
- [[Prototype]] is a delegation chain for properties on objects
- Opposite from classes where behavior is copied down -> Objects are linked to a prototype and behavior is delegated of the chain
- Lookup done with:
1. `__proto__` (public, non-standardized property)
2. `Object.getPrototypeOf()` (es5 standardized utility)
3. `obj.constructor.prototype` (property implemented pre ie 9) **referencing non-special and writeable properties**
- Any properties that are not found on current object are delegated up the chain, all the way to Object.prototype
- Bind properties to `this`
- Use `var self = this` / context, / that, when using event handlers

### OLOO Delegation
- Replace `new` with `Object.create(obj.prototype)`
- Useful when you need to create multiple instances
