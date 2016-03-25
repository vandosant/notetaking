- Code organization: https://github.com/reactjs/react-router
- Render method must return a component and (ideally) be pure (not changing variables)
- Linting: npm standard, then cli run standard; editorconfig.org
- Tree shaking: rollup.js, webpack
- `webpack file output`
- `ls -lsa` checks file sizes
- Babel 6 config
  - Create .babelrc
  - JSON syntax
  - Include presets
  - In production, include only individually, not all es2015 (e.g. disclude generators)
  - npm babel-preset-es2015
  - "presets": ["es2015"]
  - With webpack, add babel-loader `webpack --module-bind 'js=babel'`
- Webpack config
```js
const path = require('path')

module.exports = {
  context: __dirname, // provided by node
  entry: './js/ClientApp.js',
  output: {
    path: path.join(__dirname, '/public'),
    filename: 'bundle.js'
  },
  resolve: {
    extensions: ['', '.js', '.jsx', '.json'] // find require paths without extensions
  },
  stats: {
    colors: true,
    reasons: true, // verbose errors
    chunks: false
  },
  module: {
    loaders: [ // build pipeline
      {
        test: /\.jsx?$/,
        loader: 'babel-loader'
      }
    ]
  }
}
```
- http://regexr.com/

#### Unit testing
- Chai for assertions, mocha to run, enzyme for helpers
- react-addons-test-utils from facebook (enzyme dependency)
- /test directory (required by mocha)
- (alternative assertions) power assert, should
- `mocha --require test/helpers/setup.js`
- enzyme
  - shallow: only render given component, not the children
    - `var wrapper = shallow(<Component />)`
    - `wrapper.debug`
  - mount: similar to shallow with things like event simulation
  - static rendering: uses jsdom and cheerio to create a more realistic browser env
- coverage
  - istanbul
  - `npm install -g nyc`
  - `nyc --reporter=lcov --reporter=text --reporter=html --require babel-register --extension .jsx npm test`
  - `open coverage/index.html`

- hot reloading
  - live reload for css
  - does not work for stateless functional components

- flux
  - elm: simplified version of flux
  - port of elm architecture into javascript
  - one way data flow (props down)
  - upward event flow (actions up)
  - dispatcher: function that delegates actions to another function
  - delegated function updates the store
  - store updates the view
  - makes it easier to follow actions and their outcomes around
  - single data store

- redux
  - "flux middleware for multiple stores"
  - can hit critical mass at ~10 stores
  - instead of a whole new store, you add a new property to a store
  - emit an action
  - action gets called to the root reducer
  - root reducer dispatches to smaller reducers
  - "reducers all the way down"
  - reducers: takes one state, returns a new state, without modifying original state
