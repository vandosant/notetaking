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
```{
  "env": {
    "browser": true,
    "node": true,
  },
  "extends": [
    "kentcdodds/best-practices",
    "kentcdodds/possible-errors",
  ],
  "rules": {},
}```

## coverage
* nyc, with lcov reporter
* `"scripts": {"test": "nyc mocha"}`
* `"nyc": {"include": "src"}`

## validation
* git hooks + ghooks tool
* ++scripts `"validate": "npm-run-all --parallel test lint"`
* ```  "config": {
    "ghooks": {
      "pre-commit": "npm run validate"
    }
  }```
