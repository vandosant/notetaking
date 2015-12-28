### Notes From Frontend Masters [Advanced JavaScript](https://frontendmasters.com/courses/advanced-javascript/)

Resources:  
[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)  
[Style Guide](https://github.com/rwaldron/idiomatic.js/)  
[Spec](http://www.ecma-international.org/publications/standards/Ecma-262.htm)  
[Spec Proposals](http://wiki.ecmascript.org/doku.php?id=harmony:proposals)  

- Function declarations start with the function keyword
- else it is a function expression, eg var foo = function bar() {}
- Function expression variable declarations are enclosed in their own scope
- Anonymous function expression negatives
    1. No ability to self-reference
    2. Nothing to reference in debugging
    3. Less self-documentation

Scope
- Lexical scoping by default
- `catch` / `try` is block scoped
- `eval` modifies existing lexical scope
- `with` creates a lexical scope at runtime
- Let creates block scope
