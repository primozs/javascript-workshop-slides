# Modules



## Moduli
Uporaba z node-om ali webpack-om
 
```
// v abc.js
module.exports = function() {...}
module.exports = {
  b: () => {},
  c: () => {} 
}
module.exports = function(param) {...}

// v b.js
var a = require('./abc');

var a = require('./abc');
a.b();
b.c();

var a = require('./abc')(param);
```



## Moduli v ES6
```
// v abc.js
export default function () {...}
export function b() {...}
export const c = 299792458;

// v b.js
import a from "./abc";
import a1 from "./abc";
import {b, c} from "./abc";
import {b as bee, c as lightSpeed} from "./abc";
import a2, {b, c} from "./abc";
```

