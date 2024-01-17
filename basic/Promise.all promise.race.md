## The difference and usage scenarios between Promise.all and Promise.race

（1）Promise.all

Promise.all can wrap multiple Promise instances into a single new Promise instance. Additionally, the return values for success and failure are different. On success, it returns an array of results, whereas on failure, it returns the value from the first Promise that was rejected.

In Promise.all, an array is passed in, and an array is also returned. The returned values from the inputted Promise objects are mapped and arranged in the array in the order they were passed in. However, it is important to note that the execution order of these Promises is not necessarily sequential, unless the iterable object is empty.

It should be noted that the order of data in the array of successful results obtained by Promise.all matches the order of the array received by Promise.all. This is particularly useful in scenarios where multiple requests are sent and data needs to be obtained and used in the order of these requests. Promise.all can be used to handle such situations.

（2）Promise.race

As implied by its name, Promise.race is analogous to a race. It means that in Promise.race([p1, p2, p3]), whichever result is obtained first, that result is returned, regardless of whether it's a success or a failure. This method can be useful when there's a need to perform an action only within a certain time frame; if the time is exceeded, the action is no longer pursued.

```js
Promise.race([promise1, timeOutPromise(5000)]).then((res) => {});
```
