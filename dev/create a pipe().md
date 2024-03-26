## Today's topic is create a pipe()

Suppose there are some functions, as follow:

```js
const times = (y) => (x) => x * y;
const plus = (y) => (x) => x + y;
const subtract = (y) => (x) => x - y;
const divide = (y) => (x) => x / y;
```

And we need a function pipe()to combine these functions. For example:

```js
pipe([times(2), times(3)]);
// x * 2 * 3

pipe([times(2), plus(3), times(4)]);
// (x * 2 + 3) * 4

pipe([times(2), subtract(3), divide(4)]);
// (x * 2 - 3) / 4
```

First, we create a function called pipe. As you can see, the result returned by pipe actually is a function.

```js
function pipe(funcs) {
  return (x) => {};
}
```

Next, we're going to excute each of funcs sequentially. Declare a variable to save value of every time. that is result that initial value is x. Creating a for loop to loop through elements of funcs.

```js
function pipe(funcs) {
  return (x) => {
    let result = x;
    for (let fun of func) {
    }
  };
}
```

The final effect is using xto make calculation for each fun. and set the value of the funcalled to the result variable.

```js
function pipe(funcs) {
  return (x) => {
    let result = x;
    for (let fun of func) {
      result = fun.call(this, result);
    }
    return result;
  };
}
```

Finally, return result.
