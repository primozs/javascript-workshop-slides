# Babel



## Kaj je babel
- najbolši in najbolj uveljavljen javascript transpiler
- pretvarja javascript iz es6 v es5
- React JSX podpora (pretvara JSX v javascript)



## Inštalacija
```
// globalna inštalacija
$ npm install babel -g
$ npm install -g babel-cli

// v posameznem node projektu za `babel-node`
$ npm install babel-core --save-dev
$ npm install babel-preset-react --save-dev
$ npm install babel-preset-es2015 --dave-dev
$ npm install babel-preset-stage-0 --save-dev
```



## Project babel settings
```
// .babelrc
{
  "presets": ["react", "es2015", "stage-0"]
}
```



## Command line
```
// babel xfile.js 
// babel xfile.js | node

// babel-node xfile.js
```



## Reference
- <https://babeljs.io/>
- <http://babeljs.io/docs/setup/>
- <https://facebook.github.io/react/docs/tooling-integration.html>
