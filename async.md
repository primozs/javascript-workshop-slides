## Callbacks
```
var f = function(cb){
  // nekaj se izvede
  var result = 42; 
  cb(result)
}

f(function(res){
  console.log(res);
});
```
```
step1(function (value1) {
    step2(value1, function(value2) {
        step3(value2, function(value3) {
            step4(value3, function(value4) {
                // Do something with value4 
            });
        });
    });
});
```



## Promise
- promise objekti vrnejo promise objekt 
- promise ima metodo `then`, ki v prihodnosti vrne rzultat 
- emulirajo sinhroni control flow `try {} catch`
- best practice je da se na koncu vedno doda `.catch(f)`

```
doStuff(promisedStep1)
  .then(promisedStep2)
  .then(function(value){
    // something
    return promise;
  })
  .catch(function(err){
    // something
  });
```



## Promise "q"
```
// ES5: https://www.npmjs.com/package/q
var q = require('q');

function uppercasePromised(str) {
  var def = q.defer();
  var result;

  try {
    result = str.toUpperCase();
  } catch (e) {
    def.reject(e);
  }

  def.resolve(result);
  return def.promise
}

uppercasePromised(process.argv[2])
  .then(console.log)
  .catch(console.log);
```



## Promise es6
```
var promise = new Promise((resolve, reject) => {
  setTimeout(function () {
        resolve(42)
  },  500);
})

promise.then(x => console.log(x));
```



## Več promisov na enkrat v vrstnem redu
```
function msgAfterTimeout(who, timeout) {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      resolve(`Hello ${who}!`)
    }, timeout)
  });
}

Promise.all([
    msgAfterTimeout('Foo', 3000),
    msgAfterTimeout('Bar', 500)
  ])
  .then(function (result) {
    console.log(result);
  })
  .catch(function (err) {
    console.log(err);
  });
```



## References
- [es6 promise mozilla dev](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- <https://www.npmjs.com/package/q>
- [vač: promise vs. observables](https://egghead.io/lessons/rxjs-rxjs-observables-vs-promises)
- [več: reactive](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)

