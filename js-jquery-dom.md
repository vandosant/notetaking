### Notes From Frontend Masters [JavaScript JQuery DOM](https://frontendmasters.com/courses/javascript-jquery-dom)

Setup
- Install NodeJS from http://nodejs.org/
- https://docs.npmjs.com/getting-started/fixing-npm-permissions
- npm install http-server -g

Basics
 - Everything is a pointer.
 - The delete keyword does not remove objects from memory. its primary use is to de-reference objects.
 - Useful when you want to remove references to object properties.
 - The return val of delete tells you whether your syntax was correct.
 - typeof Null = "object" (wrapped in an obj in memory)
 - typeof NaN = "number"
 - typeof Array = "object" (wrapped in an obj in memory)
 - Primitives as args to functions are copied into the function scope.
 - Objects as args to functions are passed as references to the function scope.
