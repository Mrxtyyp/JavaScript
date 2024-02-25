## Implementing the apply Function Manually

Steps to implement the apply function:

1. Determine if the calling object is a function. Even though it's defined on the function's prototype, there may be instances where it is invoked using methods like call.
2. Check if the incoming context object exists; if not, set it to window.
3. Assign the function as a property of the context object.
4. Determine if the parameter values have been passed in.
5. Invoke the method using the context object and save the returned result.
6. Remove the property that was just added.
7. Return the result

```js
// apply implement
Function.prototype.myApply = function (context) {
  // context object equal to function
  if (typeof this !== "function") {
    throw new TypeError("Error");
  }
  let result = null;
  // context or window
  context = context || window;
  // save fn
  context.fn = this;
  // invoke
  if (arguments[1]) {
    result = context.fn(...arguments[1]);
  } else {
    result = context.fn();
  }
  // remove
  delete context.fn;
  return result;
};
```
