# Webpack
## module bundler



## install
```
// install command line globally
$ npm install webpack -g

// install webpack package in indivitudal project
$ npm install webpack --save-dev
$ npm install webpack-dev-server --save-dev
 
// bable loader
$ npm install babel-loader --save-dev
```



## config file
- default config file name `webpack.config.js`

```
module.exports = {
  entry: './src/main.js',
  output: {
    filename: 'bundle.js'
  },
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader'}
    ]
  }
};
```



## Celoten preprosti config
```
module.exports = {
  entry: './src/main.js',
  output: {
    path: '.dist',
    filename: 'bundle.js',
    publicPath: '/'
  },
  devServer: {
    inline: true,
    contentBase: './dist'
  },
  module: {
    loaders: [
      {
        test: /\.js$/, 
        exclude: /node_modules/, 
        loader: 'babel-loader',
        query: {
          presets: ['es2015', 'react']
        }
      }
    ]
  }
};
```



## Run it
```
// ročno
$ webpack

// dev server
$ webpack-dev-server

// v package.json
"scripts": {
  "start": "webpack-dev-server"
}

$ npm run start
```



## Webpack reference
- [project page](https://webpack.github.io/)
- [howto](https://github.com/petehunt/webpack-howto)
- [cookbook](http://christianalfoni.github.io/react-webpack-cookbook/)
- [trije članki - glej linke](http://survivejs.com/webpack_react/webpack/)
