## What are wrapper types in JavaScript?

In JavaScript, basic types have no properties and methods, but in order to facilitate the manipulation of basic type values, JavaScript implicitly converts basic type values to objects in the background when calling properties or methods of basic types, such as:

```js
const a = "abc";
a.length; // 3
a.toUpperCase(); // "ABC"
```

When accessing 'abc'.length, JavaScript converts 'abc' to String('abc') in the background, and then accesses its length attribute.

JavaScript can also use the Object function explicitly to convert primitive types into wrapper types:

```js
var a = "abc";
Object(a); // String {"abc"}
```

Using the valueOf method, it is also possible to reverse the wrapped type to the basic type.

```js
var a = "abc";
var b = Object(a);
var c = b.valueOf(); // 'abc'
```

Look at the following code to see what it will print:

```js
var a = new Boolean(false);
if (!a) {
  console.log("Oops"); // never runs
}
```

The answer is that nothing will be printed because although the package's basic type is false, once false is wrapped into a packaged type, it becomes an object, so its non-value is false, meaning the contents of the loop body will not run.
