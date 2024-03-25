## Implement a detectType function to get the value of the pass-in object.

First of all, the pass-in object can be anyone, so we have to ensure this function is suitable for anyone.
we're going to use Object.prototype.toString.call() that will return a string like '[object Object]', where the Object string is the type of the current object.
so, we just use the substring method to take in 8 and the length of the '[object Object]' minus one, and then we can get 'Object'.
Next, we just make a conversion that using the toLowercase method.
Finally, return it.

```js
/**
 * @param {any} data
 * @return {string}
 */
function detectType(data) {
  const typeStr = Object.prototype.toString.call(data);
  return typeStr.substring(8, typeStr.length - 1).toLowerCase();
}
```
