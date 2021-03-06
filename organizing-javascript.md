### Notes From Frontend Masters [Organizing Javascript](https://frontendmasters.com/courses/organizing-javascript/)

# Event Based Programming
- [Event Emitter library](https://github.com/hij1nx/EventEmitter2)

## Server-side

### Routing
#### Functions
- Push routing functions into an array
- Accepts a request and response stream
- Set headers
  - Set Server header
  - Set Content-Security-Polity
  - Set Strict-Transport-Security
- FullRequest
  - Wait until all chunks of data come in and add to request body
- Handle favicon; Cacheable 204 response
- Handle static resources
- Handle full page requests
  - See if it is one of the internal templates, if so get html and render
- Handle default route; 404 response

#### Processing
- Use a loop or a generator function to run through all routing functions with each request
- Take generator and automatically run to completion // [Asynquence](https://github.com/getify/asynquence); react function

### Modules
- Hybrid server/browser code
- Add to `global.Foo = 'Foo.js' // with some require method` in node server
- Require methods
  - UMD
  - Commonjs // use module bundler
  - AMD // use module bundler
- Add new route for Foo api // `"/Foo"` invokes and uses Foo module, returns json
