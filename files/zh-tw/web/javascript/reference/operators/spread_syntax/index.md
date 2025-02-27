---
title: Spread syntax (...)
slug: Web/JavaScript/Reference/Operators/Spread_syntax
---
{{jsSidebar("Operators")}}

**展開運算子**(`...`) 允許可迭代的陣列或字串展開成０到多個參數(如果是 function 的話)或是０到多個元素(如果是 array 或字組的話)，或如果是物件的話則展開成０到多個 key-value pair。

{{EmbedInteractiveExample("pages/js/expressions-spreadsyntax.html")}}

## 語法

用在呼叫函式時:

```plain
myFunction(...iterableObj);
```

用在陣列或字串時:

```plain
[...iterableObj, '4', 'five', 6];
```

用在物件時(new in ECMAScript 2018):

```plain
let objClone = { ...obj };
```

## Rest syntax (parameters)

Rest syntax looks exactly like spread syntax. In a way, rest syntax is the opposite of spread syntax. Spread syntax "expands" an array into its elements, while rest syntax collects multiple elements and "condenses" them into a single element. See {{jsxref("Functions/rest_parameters", "rest parameters", "", 1)}}.

## Examples

### Spread in function calls

#### Replace apply()

It is common to use {{jsxref("Function.prototype.apply()")}} in cases where you want to use the elements of an array as arguments to a function.

```js
function myFunction(x, y, z) { }
const args = [0, 1, 2];
myFunction.apply(null, args);
```

With spread syntax the above can be written as:

```js
function myFunction(x, y, z) { }
const args = [0, 1, 2];
myFunction(...args);
```

Any argument in the argument list can use spread syntax, and the spread syntax can be used multiple times.

```js
function myFunction(v, w, x, y, z) { }
const args = [0, 1];
myFunction(-1, ...args, 2, ...[3]);
```

#### Apply for new operator

When calling a constructor with {{jsxref("Operators/new", "new")}} it's not possible to **directly** use an array and `apply()` (`apply()` does a `[[Call]]` and not a `[[Construct]]`). However, an array can be easily used with `new` thanks to spread syntax:

```js
const dateFields = [1970, 0, 1];  // 1 Jan 1970
const d = new Date(...dateFields);
```

To use `new` with an array of parameters without spread syntax, you would have to do it **indirectly** through partial application:

```js
function applyAndNew(constructor, args) {
   function partial () {
      return constructor.apply(this, args);
   };
   if (typeof constructor.prototype === "object") {
      partial.prototype = Object.create(constructor.prototype);
   }
   return partial;
}


function myConstructor () {
   console.log("arguments.length: " + arguments.length);
   console.log(arguments);
   this.prop1="val1";
   this.prop2="val2";
};

const myArguments = ["hi", "how", "are", "you", "mr", null];
const myConstructorWithArguments = applyAndNew(myConstructor, myArguments);

console.log(new myConstructorWithArguments);
//  (internal log of myConstructor):           arguments.length: 6
//  (internal log of myConstructor):           ["hi", "how", "are", "you", "mr", null]
//  (log of "new myConstructorWithArguments"): {prop1: "val1", prop2: "val2"}
```

### Spread in array literals

#### A more powerful array literal

Without spread syntax, to create a new array using an existing array as one part of it, the array literal syntax is no longer sufficient and imperative code must be used instead using a combination of {{jsxref("Array.prototype.push", "push()")}}, {{jsxref("Array.prototype.splice", "splice()")}}, {{jsxref("Array.prototype.concat", "concat()")}}, etc. With spread syntax this becomes much more succinct:

```js
const parts = ['shoulders', 'knees'];
const lyrics = ['head', ...parts, 'and', 'toes'];
//  ["head", "shoulders", "knees", "and", "toes"]
```

Just like spread for argument lists, `...` can be used anywhere in the array literal, and may be used more than once.

#### Copy an array

```js
const arr = [1, 2, 3];
const arr2 = [...arr]; // like arr.slice()

arr2.push(4);
//  arr2 becomes [1, 2, 3, 4]
//  arr remains unaffected
```

> **備註：** Spread syntax effectively goes one level deep while copying an array. Therefore, it may be unsuitable for copying multidimensional arrays, as the following example shows. (The same is true with {{jsxref("Object.assign()")}} and spread syntax.)
>
> ```js example-bad
> const a = [[1], [2], [3]];
> const b = [...a];
>
> b.shift().shift();
> //  1
>
> //  Oh no!  Now array 'a' is affected as well:
> a
> //  [[], [2], [3]]
> ```

#### A better way to concatenate arrays

{{jsxref("Array.prototype.concat()")}} is often used to concatenate an array to the end of an existing array. Without spread syntax, this is done as:

```js
const arr1 = [0, 1, 2];
const arr2 = [3, 4, 5];

//  Append all items from arr2 onto arr1
arr1 = arr1.concat(arr2);
```

With spread syntax this becomes:

```js
let arr1 = [0, 1, 2];
let arr2 = [3, 4, 5];

arr1 = [...arr1, ...arr2];
//  arr1 is now [0, 1, 2, 3, 4, 5]
// Note: Not to use const otherwise, it will give TypeError (invalid assignment)
```

{{jsxref("Array.prototype.unshift()")}} is often used to insert an array of values at the start of an existing array. Without spread syntax, this is done as:

```js
const arr1 = [0, 1, 2];
const arr2 = [3, 4, 5];

//  Prepend all items from arr2 onto arr1
Array.prototype.unshift.apply(arr1, arr2)

//  arr1 is now [3, 4, 5, 0, 1, 2]
```

With spread syntax, this becomes:

```js
let arr1 = [0, 1, 2];
let arr2 = [3, 4, 5];

arr1 = [...arr2, ...arr1];
//  arr1 is now [3, 4, 5, 0, 1, 2]
```

> **備註：** Unlike `unshift()`, this creates a new `arr1`, and does not modify the original `arr1` array in-place.

### Spread in object literals

The [Rest/Spread Properties for ECMAScript](https://github.com/tc39/proposal-object-rest-spread) proposal (ES2018) added spread properties to {{jsxref("Operators/Object_initializer", "object literals", 1)}}. It copies own enumerable properties from a provided object onto a new object.

Shallow-cloning (excluding prototype) or merging of objects is now possible using a shorter syntax than {{jsxref("Object.assign()")}}.

```js
const obj1 = { foo: 'bar', x: 42 };
const obj2 = { foo: 'baz', y: 13 };

const clonedObj = { ...obj1 };
// Object { foo: "bar", x: 42 }

const mergedObj = { ...obj1, ...obj2 };
// Object { foo: "baz", x: 42, y: 13 }
```

Note that {{jsxref("Object.assign()")}} triggers {{jsxref("Functions/set", "setters")}}, whereas spread syntax doesn't.

Note that you cannot replace or mimic the {{jsxref("Object.assign()")}} function:

```js
let obj1 = { foo: 'bar', x: 42 };
let obj2 = { foo: 'baz', y: 13 };
const merge = ( ...objects ) => ( { ...objects } );

let mergedObj1 = merge (obj1, obj2);
// Object { 0: { foo: 'bar', x: 42 }, 1: { foo: 'baz', y: 13 } }

let mergedObj2 = merge ({}, obj1, obj2);
// Object { 0: {}, 1: { foo: 'bar', x: 42 }, 2: { foo: 'baz', y: 13 } }
```

In the above example, the spread syntax does not work as one might expect: it spreads an _array_ of arguments into the object literal, due to the rest parameter.

### Only for iterables

Objects themselves are not iterable, but they become iterable when used in an Array, or with iterating functions such as `map()`, `reduce()`, and `assign()`. When merging 2 objects together with the spread operator, it is assumed another iterating function is used when the merging occurs.

Spread syntax (other than in the case of spread properties) can be applied only to [iterable](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator) objects:

```js
const obj = {'key1': 'value1'};
const array = [...obj]; // TypeError: obj is not iterable
```

### Spread with many values

When using spread syntax for function calls, be aware of the possibility of exceeding the JavaScript engine's argument length limit. See {{jsxref("Function.prototype.apply", "apply()")}} for more details.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat("javascript.operators.spread")}}

## See also

- {{jsxref("Functions/rest_parameters", "Rest parameters", "", 1)}} (also ‘`...`’)
- {{jsxref("Function.prototype.apply()")}} (also ‘`...`’)
