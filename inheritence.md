# Inheritance
## Planet proto vaje
```
npm install planetproto -g
```



## Kako ustvarjamo objekte
```
// classical using new
var obj = new Object();

// object literal
var obj = {};
```



## object literal
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



## __proto__ object property
- ni del standardnega api-ja zato ga v svoji kodi ne uporabljamo

```
var alien = {
  kind: 'alien'
};
    
var robot = {
  kind: 'robot'
};

var zippy = {};

zippy.__proto__ = alien;
console.log(zippy.kind); //=> 'alien'

zippy.__proto__ = robot;
console.log(zippy.kind); //=> 'robot'
```



## Poizvedovanje za lastnostmi in metodami je dinamično
- objekt delegira poizvedbo na svoj prototip
- objekti si lahko delijo isti prototip

```
var alien = {};    
var zippy = {};
zippy.__proto__ = alien;

console.log(zippy.kind); //=> undefined

alien.kind = 'alien';
console.log(zippy.kind); //=> 'alien'
```



## Lastnosti na objektu in na prototipu
```
var alien = {
  kind: 'alien'
};

var zippy = {};
zippy.__proto__ = alien;

zippy.kind = 'zippy';

console.log(zippy.kind); //=> 'zippy'
console.log(alien.kind); //=> 'alien'
```



## Tabele in objekti na prototipu
- načeloma ne nastavljaj state-a na prototipu

```
var alien = {
  skills: ['morph']
};

var zorg = {};
zorg.__proto__ = alien;

zorg.skills.push('clone');

console.log(zorg.skills);  //=> morph, clone

console.log(alien.skills); //=> morph, clone
```



## Delegation prototype inheritance
- Object.create in Object.assign
 
```
// namesto __proto__ in state-a na prototipu

// delegate prototype
let animal = {
  animalType: 'animal',
  describe(){
    return `an ${this.animalType} with ...`
  }
};

// instance 
let mouse = Object.assign(Object.create(animal), {
  animalType: 'mouse',
  furColor: 'white',
  lets: 4
})
```



## Is proto of, get proto of 
```
var alien = {
    kind: 'alien'
};
var zack = Object.create(alien);

alien.isPrototypeOf(zack) // true
Object.getPrototypeOf(zack) // Object {kind: "alien"}
```



## Clone/concatenate mixins inheritance
- to use as default or override 
- properties will be copied over 

```
var proto = {
  hello: function() {
    return 'Hello, my name is ' + this.name;
  }
};
var george = Object.assign({}, proto, {name: 'George'});
```



## "Functional prototype inheritance" - factory
- "kontstruktor funkcija"
- funkcija, ki definira in vrača objekte
- dobro za enkapsulacijo in privatne spremenljivke, state je privaten



## "Functional prototype inheritance" - factory 
```
var model = function(name) {
  var state = {};
  state.name = name;

  return {
    getName() {
      return state.name;
    },

    setName(name) {
      state.name = name;
    }
  };
};
```



## Instances 
```
var a = model('alibaba');
console.log(a.getName()); // alibaba

a.setName('alibaba1');
console.log(a.getName()); // alibaba1

var b = model('franci');
console.log(b.getName()); // franci

b.setName('franci1');
console.log(b.getName()); // franci1
```



## More factory example
```
let animal = { // prototip
  animalType: 'animal',
  
  describe(){
    return `an ${this.animalType} with ...`
  }
};
```
```
let mouseFactory = function mouseFactory() { // factory
  let someOtherPrivateVar = 'foo';
  
  return Object.assign(Object.create(animal), {
    animalType: 'mouse',
    furColor: 'white',
    lets: 4,
    getFoo() {
      return someOtherPrivateVar; 
    }
  });
};

let mickey = mouseFactory();
```



## Composition over inheritance
```
const barker = (state) => ({
  bark: () => console.log('Woof, I am ' + state.name)
})
const driver = (state) => ({
  drive: () => state.position = state.position + state.speed
})
```

```
const murderRobotDog = (name)  => {
  let state = {
    name,
    speed: 100,
    position: 0
  }
  return Object.assign(
        {},
        barker(state),
        driver(state),
        killer(state)
    )
}
const bruno =  murderRobotDog('bruno')
bruno.bark() // "Woof, I am Bruno"
```



## Javascript classical inheritance
```
// Constructor funkcija
function Parent() {
  this.a = 42;
}

// metode definiramo na prototipu
Parent.prototype.foo = function foo() {};

// nove instance z `new` rezervirano besedo
var pObj = new Parent();
```
```
function Child() {
  Parent.call(this);
  this.b = 3.14159
}

Child.prototype = Object.create(Parent.prototype);
Child.prototype.constructor = Child;

Child.prototype.foo = function foo() {
  Parent.prototype.foo.call(this);
};

this.instance = new Child();
```
[closure library goog.inherits](https://github.com/google/closure-library/blob/master/closure/goog/base.js#L2223)



## Function prototype
```
function Alien() {}
    
Alien.prototype;
Alien.prototype === Alien.__proto__ // false
Alien.__proto__ == Function.prototype // true

// Alien.prototype se nastavi na novo instanco
var et = new Alien()
et.__proto__ == Alien.prototype // true
```



## Kaj naredi `new` 
- ustvari novo instanco objekta
- zažene konstruktor funkcijo
- bind `this` na novo instanco
- naredi referenco prototipa novega objekta na prototip 
objekta konstuktor funkcije `objInstance.__proto__`  
- poimenuje tip objekta po imenu konstruktor funkcije, omogoči `instanceof` 



## ES6 classes
```
class Parent {
  constructor() {
    this.a = 42;
  }
  
  foo() {}
}

var pObj = new Parent();
```
```
class Child extends Parent {
  constructor(){
    super();
    this.b = 3.14159; 
  }
  
  foo() {
    super.foo();
  }
}
```
[class inheritance](http://es6-features.org/#ClassInheritance)



## Inheritance refs.
- <http://www.objectplayground.com/>
- [common misconceptions about inheritance in JS](https://medium.com/javascript-scene/common-misconceptions-about-inheritance-in-javascript-d5d9bab29b0a)
- [how to fix the class keyword](https://medium.com/javascript-scene/how-to-fix-the-es6-class-keyword-2d42bb3f4caf)
- [book chapter](http://chimera.labs.oreilly.com/books/1234000000262/ch03.html#delegate-prototype)
- [composition over inheritence](https://medium.com/humans-create-software/composition-over-inheritance-cb6f88070205)
