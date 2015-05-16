SymbolMirror
=========

Constructs an enumeration with symbols as values and keys, in addition to original keys.

Inspired by `react/lib/keyMirror` through https://github.com/STRML/keyMirror.

Useful when extending es6 classes to avoid overriding inherited methods.

Usage
-----

`npm install symbolMirror`

```javascript
var symbolMirror = require('symbolMirror');
var COLORS = keyMirror({blue: null, red: null});
var myColor = COLORS.blue;
var isColorValid = !!COLORS[myColor];
```

Last line is possible due to generated enum having keys as the same symbols as the original keys' values.

```javascript

var symbolMirror = require('symbolMirror');
var actions = symbolMirror({myMethod: null});

class MyClass {
	myMethod(...args) {
		// do something with 'args'
	}
}

class MyExtendedClass extends MyClass {
	[actions.myMethod](...args) {
		//do something else with 'args'
	}
}
```

With keyMirror, the above would cause the original `myMethod` to be overriden, which is not always desired.

Input:  `{key1: val1, key2: val2}`

Output: `{key1: symbol1, key2: symbol2, symbol1: symbol1, symbol2: symbol2}`
