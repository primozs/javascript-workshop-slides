# Node



## Hello world
```
// program.js
console.log('HELLO WORLD');

$ node program.js
```



## Argumenti

```
$ node program.js 1 2 3

// arg. array
process.argv

[ 'node', '/path/to/your/program.js', '1', '2', '3' ]

// seštej 1, 2, 3
var args = process.argv;

console.log(args.slice(2).reduce(function(sum, item){
  return sum += Number(item);
}, 0));
```



## IO
```
// fs.readFileSync
// fs.readFile
// fs.readdir

// beri datoteko sinhrono
var fs = require('fs');
var content = fs.readFileSync(process.argv[2]).toString();

// beri datoteko asinhrono
var fs = require('fs');
var path = process.argv[2];

fs.readFile(path, {}, function (err, data) {
  console.log(data.toString())
});
```



## http server
```
var http = require('http');
var port = process.argv[2] || 3000;

var server = http.createServer(function (req, res) {
  if (req.method === 'GET') {
    res.write('Hello world');
    res.end();
  }
});

server.listen(port, function () {
  console.log('listening at', port)
});
```



# Express



## Express-hello project
Branch step1 - hello world server



## Gulp task runner
```
$ npm install gulp --save-dev
$ npm install gulp -g
$ npm install gulp-nodemon --save-dev
```



## Branch step2 
- serve file

```
res.status(200).sendFile('..../public/hello.html'));
```



## Branch step3 
- serve static files

```
app.use('/', express.static('./public')));
```



## Branch step4 
- render with render engine

```
gaikan.options.layout = 'layout';
app.set('view engine', 'html');
app.engine('html', gaikan);

app.get('/about', function (req, res) {
  res.render('about', {author: 'Taras Bulba'});
});
```



## Branch step5 
- Router, 
- get, post form 
- params, query



## React 
- Branch step-6, react serverside 
- Branch step-7, react server and client



## Express-rest-hello 
- pregled
