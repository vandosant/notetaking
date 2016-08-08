webpack

- a module bundler
- emulated a module loader

- everything is a module
- dependencies are explicitly required — everything that is in the file, you have

- was created in order to do code splitting with a bundler tool
- inspired by gwit google web toolkit

shortcomings
- dependency on javascript
- (not great for css, for ex)

getting started
- start small
- react webpack cookbook
- understand core terminology and concepts
- embrace being a beginner
- build from there

terms
==
entry:  
output:  
loader
- function that gets an input and returns an output (usually async)
- for doing transformations
- takes some file and returns another file
- must be chained in the right order
- akin to typing
- ex: babel loader (src code) -> return transpiled js
- ex: css (less-loader) -> (css-loader) -> string -> (style-loader)

plugin
- html webpack plugin
- when you want to change the chunking, where modules are in the chunk tree
- everything related to the compilation process
- allow you to work with compilations — the finished result of a loader
- a more complete api to what web pack does
- implements the tappable class

hot module reloading
- diffs your changes and only loads them instead of everything

tree shaking
- unused/dead code elimination
- rollup js
- closure compiler (in advanced mode, with js doc annotations)
- webpack 2 + ES2015 modules, instead of common js modules
- transforms unused modules into dead code
- tracks import and export statements and knows which ones are never used,
- modules are removed when transpiled by uglify js

webpack 2 
- [gist](https://gist.github.com/sokra/27b24881210b56bbaff7?utm_source=javascriptweekly&utm_medium=email)
- es6 module syntax
- allow for:
- use tree shaking for css

webpack validator tool
- runtime linter
- lets you know if you make mistakes
- lets you know if you are using good or bad practices

don't do everything
- babel plugin for aliases in webpack

tips
- do not abstract configs
- webpack environment online

es6
http://www.2ality.com/2016/05/six-nifty-es6-tricks.html

===
FEM
===

webpack 2.1.0

https://www.npmjs.com/package/webpack-validator
https://webpack.github.io/docs/webpack-dev-server.html

CSS Loader > JS > Style Loader (at runtime)
https://github.com/webpack/style-loader

- now loads css at bundle
- can implement critical css for what you need. js for the rest.
