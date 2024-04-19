## implement-once

The once function just like lodash.once. \_.once(func) is used to force a function to be called only once, later calls only returns the result of first call.

```js
function func(num) {
  return num;
}

const onced = once(func);

onced(1);
```

we need to do two things, one is save the result of first call, two is the function be called only once.
we're going to declare two variables: isCall and result. isCall means if the function is called. result is used to store the result of first call.
The once function must return a fucntion as the oncedcan be called. it's use apply method to perform the func, then set the value of result equal to the result of the function call.
Change isCallto true, it will return the result when funciton is called again.

```js
/**
 * @param {Function} func
 * @return {Function}
 */
function once(func) {
  let isCall = false;
  let result = null;
  return function (...args) {
    if (isCall) return result;
    result = func.apply(this, args);
    isCall = true;
    return result;
  };
}
```
