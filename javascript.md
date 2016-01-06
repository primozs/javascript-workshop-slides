# JavaScript 



## Spremenljivke
```
  var example = 'foo';
```
- ime spremenljivke se mora pričet z alpha caracterjem
- javascript je case sensitive `a1 !== A1`
- če spremenljivki ne določimo `var, let, const` je avtomatsko globalna
- globalna spremenljivka je v browserju na `window` v node-u na `global` objektu



## Vrste spremenljivk
- `var` ne upošteva block scopa (es5)
- `let` upošteva block scope (es6)
- `const` ne dovoli redeklaracije (es6)
- [članek var let or const](https://medium.com/javascript-scene/javascript-es6-var-let-or-const-ba58b8dcde75)



## Tipi spremenljivk

- Undefined - undefined
- Null - null
- Number - 3.14159 
- String '', "", ``
- Boolean 
- Object {}
- Funtion function(){}
- Array []

Pomagamo si lahko z `typeof`



## Ali je undefined
```
var a;
if (a === undefined) {}
// true
```



## Ali je null
```
var a = null;
if (a === null) {}
// true
```



## Ali je number
```
isNaN(x)
```



## String narekovaji  
```
var a = 'isto';
var a = "isto"; 

// (fajn se je odločit za ' in se jih držat)
// primerjave vedno po vrednosti in tipu (!==) 

var b = `Nek string ${variable} z spremenljivko` (es6)
``` 



## String operacije
```
var str = 'some string';

str.length // 11

str.repeat(2) // "some stringsome string"

str.replace('some', 'nek') // "nek string"

str.slice(1,6) // "ome s"

str.indexOf('str') // 5
```



## Numbers
```
var roundUp = 1.5;
var rounded = Math.round(roundUp);
console.log(rounded);
```



## Cast number to string
```
var n = 128;
n.toString();

// ali pa

var x = String(n);
console.log(x);
```



## Flow, type check
- cli: `flow init, flow check`

```
/* @flow */

function foo(x: string, y: number): string {
  return x.length + y;
}

foo('Hello', 43);
```

- <http://flowtype.org/>
- <https://www.youtube.com/watch?v=9U4_hlnaFEE>




## If stavek
```
if (n > 1) {  
 console.log('the variable n is greater than 1.');  
} else {  
 console.log('the variable n is less than or equal to 1.');  
}    
```



## Ternary operator
```
var x = (n > 1) ? n : 1;
```



## switch
```
switch(variable){
  case 'xxx':
    // do something
    // break; or return 
  default:
    return;       
}
```



## for loop
```
for (var i = 0; i < 10; i++) {  
 // log the numbers 0 through 9  
 console.log(i)  
}
  
var a = [1, 2, 3];
a.forEach(function(item){
  return item * 2;
});
```



## Arrays
```
var a = ['aaa', 'bbb', 12];
var item  = a[2] // 12
```

### nekaj metod:
 
```
// filter, map, reduce, slice, join, indexOf,
// length, concat, forEach, some, find
```



## Array.filter
```
var a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
var b = a.filter(function(item) {
  return item % 2 === 0
});
console.log(b)
```



## Array.filter in map
```
var a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
var b = a.filter(function(item) {
  return item % 2 === 0
}).map(function(item){
  return item * 2;
});
console.log(b)
```



## Reduce - filter in map skupaj
```
var a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
var b = a.reduce(function(agg, item) {
  if(item % 2 === 0) {
     agg.push(item * 2);
  }
return agg;
}, [])
console.log(b)
```



## JS reference
- [javascript mozilla dev](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
