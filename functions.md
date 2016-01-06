# Funkcije 



## Kaj lahko počnemo z funkcijami
- funkcije lahko nastavimo na spremenljivke `var f = function() {}`
- vstavimo v druge funkcije - (higher order funkcije)
- vrnemo funkcije iz drugih funkcij



## Function statement
```
function myFunc(a, b) {
  return 42;
}
```



## Function expression
Funkcijo lahko nastavimo na spremenljivko 

(referenca na objekt)

```
var myFunc = function (a, b) {
  return 42;
}
``` 



## function hoisting
### function statement

```
function hereOrThere() {
  return 'here';
}

alert(hereOrThere()); // alerts 'there'

function hereOrThere() {
  return 'there';
}
```



## function hoisting
### function expression

```
var hereOrThere = function() {
  return 'here';
};

alert(hereOrThere()); // alerts 'here'

hereOrThere = function() {
  return 'there';
};
```



## Funkcije so objekti 
- nekaj funkcinih property-jev 
  - name (ime funkcije)
  - length (štefilo parametrov)
  - prototype (function prototype, na novo instanco)
  - prototype.constructor (kaže na orig. funkcijo)
  - funkciji lahko dodelimo nove property-je



## Funkcija in `this`
- ko kličemo funkcijo `obj.func()` je `obj` "receiver" `this` se nastavi na `obj`
- ko ni explicitnega receiverja `func()` takrat je `this` global obj. `window`



## Funkcija in `this`
```
function myMethod() {
  return this.val;
}

var object1 = {
  get: myMethod,
  val: 42
}

var object2 = {
  get: myMethod,
  val: 3.14159
}
```



## Funkcija in `this`
```
object1.get(); // 42
object2.get(); // 3.14159
myMethod(); // undefined

myMethod.call(object1); //42
myMethod.call(object2); //3.14159
 
myMethod.apply(object1); //42
myMethod.apply(object2); //3.14159
```



## Function context `call, apply`
- vse funkcije imajo `call` in `apply` metode
- edina razlika med tema metodama je kako funkcija sprejme parametre

```
//function addValues(a,b,c ali pa arrayVar){
// this === obj ki smo ga bindali z call oz. apply
//}

// posamezni argumenti
addValues.call(obj, 10, 20, 30);

// kot array
addValues.apply(obj, [10, 20, 30]);
```



## Funkcijin kontekst
```
var a = {

  myOnClick: function() { 
    var log  = function(n) {
      // funkcija log ima globalni window context
      console.log(this)
    }
    log();  
  }
  
};
```



to lahko rešimo z closurejem `var self = this`;

```
var a = {
  myOnClick: function() {
    var self = this;
   
    var log = function(n) {
       // funkcija log ima globalni window context
       // namesto this uporabljamo self
       console.log(self)
    }
    log();  
  }
  
};
```



ali pa z bind propertijem na funkciji

```
var a = {
  myOnClick: function() {
    var log  = function(n) {
       // funkcija log ima bindan object literal context
       console.log(this)
    }.bind(this);
    
    log();  
  }
  
};
```



## Arrow funkcije (es6)
- arrow funkcija deklarirana z "=>" je vedno anonimna
- ime funkcije dobimo z name propertijem na function objektu `function.name`
- za rekurzijo je boljša upraba klasične definicije

```
// klasično
var funkcija = function(n) {
  return n * 2;
}

// es6
var funkcija = (n) => n * 2;
```



## arrow funckije imajo avtomatski context
- arrow funkcije avtomatično bindajo funkcijin context na zunanji kontekst

```
var a = {
  myOnClick() {
    var log  = (n) => {
       console.log(this)
    };
    
    log();  
  }
  
};
```



## več o arrow funkcijah
- minimalna arrow funkcija `n => n * 2`
- če imamo več parametrov moramo uporabiti `(a, b) => a * b`
- če imamo več vrstic v body-ju funkcije uporabimo zavite oklepaje in return

```
let f = (a, b) => {
 return a * b;
};
```



## Funckijski parametri default value (es6)
```
function func(a = 1, b = null) {}
```
