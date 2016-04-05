* mountain testing - drastic variation from the current

### test mapping
```javascript
{
  "rules": ["PaymentTest(1)"],
  "templateName": "payment_cell1"
}
```

### rules engine
- boil down test to a boolean
- am I in test #10?

### template resolver
- parent template asks for a child template
- map to resolver module, evaluate rule and resolve to template partial
- return resolved partial to template engine, return to parent

### modules
- js
- css
- templates

### server rendering
- rendering: conditionally include modules based on user's test status (e.g. inNewSearch)
- build time: explicitly require dependencies and statically analyze and include them into a unique registry
```javascript
"app.js": {
  "deps": ["jquery", "newSearch.js"]
  "depsFull": ["jquery", "newSearchDep1.js", "newSearchDep2.js", "newSearch.js"]
}
```
