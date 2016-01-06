# Nekaj es6 fičerjev



# Template string ``
```
console.log(`${greeting} to you ${name}!`);
```



# Funkcije in default parametri
```
function sayHello(greeting = "Hello", name = "CampJS") {
  console.log(`${greeting} ${name}!`);
}
```



# Spread
```
var numbers = [1, 1, 2, 3, 5, 8];
var max = Math.max(...numbers);
```



# Rest
```
function sum(...args) {
  var result = 0;
  args.forEach(function (value) {
      result += value;
  });

  return result;
}

sum(1, 2, 3); // 6
```



## Destructuring
- ekstraktanje vrednosti iz objektov

```
var [ a, b ] = [1,2,3];
console.log(a, b);
// 1, 2

var [a, ...b] = [1,2,3];
console.log(a,b)
// 1, [2,3]

var { user: x } = {user: 5};
console.log(x);
// 5

var { user } = {user: 5}
console.log(user);
// 5
```



## Kdaj bi uporabili destructuring
```
var { title, subtitle } = this.props;

// ali pa kot option parametre

var Component = function ({title, subtitle}) {
  return (
    <div>
       <h1 ref="header">{title}</h1>
       <h2 ref="subheader">{subtitle}</h2>
    </div>
  );
}
```
