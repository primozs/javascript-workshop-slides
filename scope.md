# Scope



## Global in local scope
- spremenljivka deklarirana zunaj funkcijinega bloka je globalna (aVariable)
- spremenljivka deklarirana znotraj funkcije je lokalna "bVariable" lexical sc. 
- bVariable ni dostopna izven funkcije

```
var aVariable;

function someFunc() {
  var bVariable;
}
```

- es6 - block scope {}

```
if (true) {
  let aVariable;
}
```



# Scope chains
- notranji scopi lahko dostopajo zunanje ne pa obratno

```
function someFunc() {
  function inner() {
  }
  function inner2() {
    function foo() {
    }
  }
}

someFunc()
 ↑
  \
 inner2()
   ↑
 foo()
```



# Global scope
- v browserju 'window' v nodu 'global'

```
// tukaj imamo dve globalni spremenljivki 
var glob;

function someFunc() {
   var scopedVar = 1;
   function inner() {
      foo = 2;
   }
}
```



# Shadowing
```
function someFunc() {
 var foo = 1;
 function inner() {
    var foo = 2;
 }
}
```



## Closure
V javascriptu se closure naredi ko funkcija dostopa do spremenljivke izven
funkcije.

```
var count = 0;

var counter = function () {
  return count + 1;
}
```



## Closure
```
var counter = function () {
  var count = 0;
  
  return {
    getCount: function() {
      return count;
    }, 
    increment: function() {
      count += 1;
    }
  };
}
```



## IIFE, Immediately Invoked Function Expression
is a common pattern for creating local scopes
```
(function(){ // the function expression is surrounded by parenthesis  
   // variables defined here  
   // can't be accessed outside  
})(); // the function is immediately invoked
```


