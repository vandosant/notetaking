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
