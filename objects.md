# Objekti
```
var obj = {
  a: undefined,
  b: null,
  c: true,
  d: 'foo',
  e: 3.14.159,
  f: function(){},
  g: {h: 'bar'}
};
```



## Kaj je objekt
- množica key value parov (asociative array) 
- `key` property, ime mora bit string
- `value` je lahko kateregakoli tipa



## Value, Reference
- primitivni tipi se prenašajo po vrednost objekti po referenci

```
var num1, num2;
num1 = 3,
num2 = num1;
num2 = 42;
// num1 je še vendno 3

// ----

var obj1, obj2;
obj1 = {
  a: 'a'
};

obj2 = obj1;

// obe spremenljivki kažeti na isti objekt
```



## Object properties
```
var obj = {};

obj.a; // undefined (v seznamu ni "a" propertija)
obj.c = undefined'; (v seznamu je property "c")
obj.foo = 'bar';
obj['color'] = 'blue';

// if (obj.a === undefined)
// test bi za obje.a in obj.c vrnil `undefined`

// access property
console.log(obj.foo);
console.log(obj['foo']);
```
Seznam lastnosti objekta dobimo z uporabo `Object.keys(someObj)`



## Kako ustvarjamo objekte

```
// classical using new
var obj = new Object();

// najbolj pogosto
var obj = {};
```



## object literal
- posamezen objekt kot object literal 
- propertiji se določijo ob deklaraciji

```
var mouse = {
  color: 'white',
  legs: 4,
  'foo': 'bar', // slabo za compiler
  describe() {
    return `a mouse ${this.color} color with ${this.legs} legs`
  }
};
```
