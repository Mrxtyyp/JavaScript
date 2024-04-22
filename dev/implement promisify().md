## implement promisify()

Let's take a look at following error-first callback.

```js
const callback = (error, data) => {
  if (error) {
    // handle the error
  } else {
    // handle the data
  }
};
```

Now think about async functions that takes above error-first callback as last argument.

```js
const func = (arg1, arg2, callback) => {
  // some async logic
  if (hasError) {
    callback(someError);
  } else {
    callback(null, someData);
  }
};
```

You see what needs to be done now. Please implement promisify() to make the code better.

```js
const promisedFunc = promisify(func);

promisedFunc()
  .then((data) => {
    // handles data
  })
  .catch((error) => {
    // handles error
  });
```

Obviously, the promisify function need to return a function that wraps a promise instance.

```js
function promisify(func) {
  return function (...args) {
    return new Promise((resolve, reject) => {});
  };
}
```

Next, we need to perform the func funciton by call method. because it may be cannot access variable in func.

```js
function promisify(func) {
  return function (...args) {
    return new Promise((resolve, reject) => {
      func.call(...args, (error, data) => {});
    });
  };
}
```

And we're going to make a judgement if error is null. if so, reject error, if not, resolve data.

```js
/**
 * @param {(...args) => void} func
 * @returns {(...args) => Promise<any}
 */
function promisify(func) {
  return function (...args) {
    return new Promise((resolve, reject) => {
      func.call(this, ...args, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    });
  };
}
```
