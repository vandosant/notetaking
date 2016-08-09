# Writing an open source javascript library

ex: https://github.com/kentcdodds/starwars-names [FEM branches]

## Docs
* README
* LICENSE
* CODE OF CONDUCT

## npm
* npm init
* package.json
* .npmrc file
* `npm config set init-author-name "Scott Skender"`
* `npm config set init-author-email ""`
* `npm config set init-author-url ""`
* `npm config set init-license "MIT"`
* https://docs.npmjs.com/misc/config
* save-exact locks version of dependencies

## linting
* eslint
* ++scripts `"lint": "eslint src"`
```json
{
  "env": {
    "browser": true,
    "node": true,
  },
  "extends": [
    "kentcdodds/best-practices",
    "kentcdodds/possible-errors",
  ],
  "rules": {},
}
```

## coverage
* nyc, with lcov reporter
* `"scripts": {"test": "nyc mocha"}`
* `"nyc": {"include": "src"}`

## validation
* git hooks + ghooks tool
* ++scripts `"validate": "npm-run-all --parallel test lint"`
```json
"config": {
    "ghooks": {
      "pre-commit": "npm run validate"
    }
}
```

## build + transpile
+    "babel-cli": "6.11.4",
+    "babel-preset-es2015": "6.9.0"
```
  "babel": {
    "presets": [
      "es2015"
    ]
  }
```
++ scripts:
```
    "prebuild": "rimraf dist",
    "build": "babel --copy-files --out-dir dist --ignore *.test.js src",
    "validate": "npm-run-all --parallel test lint build"
```
```
  "main": "dist/index.js",
  "files": [
    "dist"
  ]
```

## dependencies
* greenkeeper.io
* david

## packaging
* gen zip:`npm pack`
* `open [packagename]`
* `require('./packagename')`
* export default api
* module.exports = api
