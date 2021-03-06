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

### Arrow functions
- function() {return 2};
- () => 2; // () => return 2;
- x => {}; // (x) => {};
- gives lexical binding of this, so cannot use in a constructor call
- always anonymous


### Default parameters
- function(a = 3) {}
- function(a = getNum()) {}

### Classes
- Safety school proposal in ES6
- class Foo{};
```javascript
var maryAge = Symbol();
class Mary{
  constructor(age, health) {
    this.health = health;
    this[maryAge] = age;
  }
  
  get isSeniorCitizen() {
    return this[maryAge] > 65;
  }
};
// export Mary

// somewhere else,
// import Mary
var m = new Mary(88, 7);
console.log(m[maryAge]);
console.log(m.isSeniorCitizen);
m['nickname'] = "Marzy";
console.log(m.nickname);
```
### Collections
Sets
```javascript
var set = new Set();
set.add(1);
set.add(2);
set.add(2);
for (let num of set) {
  console.log(num); // 1 2
}
console.log(set.size) // 2
set.clear();
console.log(set.size); // 0
```
Map
```javascript
var map = new Map();
map.set('name', 'Scott');
map.get('name'); // Scott
map.has('name') // true

// objects as keys
var user1 = {name: 'Scott', id: 123};
map.set(user1, "yo");
console.log(map.get(user1));

map.entries(); // MapIterator
map.size // 2
```
WeakMap
- Weak reference to a key; reference is released if it is the only object holding onto it.
```javascript
var weak = new WeakMap();

weak.set({name: 'Scott'}, 123);
weak.get('name');
weak.size; // undefined
```

### Promises


### Generators
```javascript
function *three() {
  yield 1;
  yield 2;
  return 3;
}

var gen = three();
gen.next(); // {value: 1, done: false}
gen.next(); // {value: 2, done: false}
gen.next(); // {value: 3, done: true}
gen.next(); // {value: undefined, done: true}


for (let v of three()) {
  console.log(v); // 1 2
}

function *foo(x) {
  var y = 2 + (yield (x + 1));
  var z = yield (y * 2);
  console.log(z, y, x)
  return x + y + z;
}

var gen = foo(5);
gen.next();
gen.next(3); // value:6
console.log(gen.next(6)); // value: 16
```
