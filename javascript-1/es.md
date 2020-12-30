---
description: ECMAScript (European Computer Manufacturer’s Association)
---

# ES

ECMAScript is a Standard for a scripting languages. It is the core that builds JavaScript.

 Languages such as ActionScript, JavaScript, JScript all use ECMAScript as its core. As a comparison, AS/JS/JScript are 3 different cars, but they all use the same engine. 

EcmaScript has different versions, to see what is compatible with different web browsers we can use websites like [https://caniuse.com/](https://caniuse.com/)

to make work modern code on older engines there are two tools: Transpilers and Polyfills.

### Transpilers

 A transpiler is a special piece of software that can parse \(“read and understand”\) modern code, and rewrite it using older syntax constructs, so that the result would be the same.

### Polyfillls

New language features may include not only syntax constructs and operators, but also built-in functions.

As we’re talking about new functions, not syntax changes, there’s no need to transpile anything here. We just need to declare the missing function.

polyfill is a script that updates/adds new functions. It “fills in” the gap and adds missing implementations.

## ES Update versions

### \*\*\*\*[**ES6 / ES2015**](https://www.greycampus.com/blog/programming/java-script-versions)\*\*\*\*

* Standard Modules — `import` and `export`
* Standardised Promises
* Classes & Inheritance
* Block-scoped variables — `let`and `const`
* Template Literals
* Object destructing into variables
* Generator functions
* Map and Set data structures
* Internationalisation for Strings, Numbers and Dates via `Intl` API

### [ES7 / ES2016](https://www.greycampus.com/blog/programming/java-script-versions)

* Array.includes\(\)
* Numeric exponent \(power of\) operator `**`

### [ES8 / ES2017](https://www.greycampus.com/blog/programming/java-script-versions)

* Async Functions
* Object.entries
* String padding functions

### [ES9 / ES2018](https://www.greycampus.com/blog/programming/java-script-versions)

* Object Rest/Spread `const obj = { ...props };`
* Asynchronous Iteration `for await (...) {`
* Promise `finally()` function
* Regular expression enhancements \(lookbehind, named groups\)



### [ES10 / ES2019](https://medium.com/@selvaganesh93/javascript-whats-new-in-ecmascript-2019-es2019-es10-35210c6e7f4b)

* Array.prototype.{flat, flatmap}
* String.prototype.{trimStart,trimEnd, matchAll}
* Object.fromEntries
* Function.prototype.toString
* Sysmbol.prototype.description
* Optional catch binding
* JSON superset
* well-formed JSON.stringify

### [ES11 / ES2020 ](https://medium.com/codingtown/ecmascript-2020-aka-es-11-9c547f69d96f)

* BigInt
* import\(\)
* Promise.allSettled\(\)
* globalThis
* Nullish Coalescing Operator `??`
* Optional Chaining Operator `?.`













