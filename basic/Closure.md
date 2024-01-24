## Understanding of closure

A closure is a function that has access to variables in another function scope. , the most common way to create a closure is to create another function within one function. The created function can access the local variables of the current function.

Closure has two common uses;

1. the first purpose of closure is to enable us to access variables inside the function outside the function. By using a closure function, you can call a closure function externally to access variables inside the function externally. You can use this method to create private variables.

2. another purpose of closure is to keep the variable object in the context of the function that has already finished running in memory. Because closure functions retain the reference of this variable object, this variable object will not be recycled.

For example, function A has A function B inside, function B can access the variables in function A, then function B is A closure.

In JS, closure allows us to indirectly access variables inside a function. Classic interview questions: use closure in loops to solve the problem of var defining functions

```js
for (var i = 1; i <= 5; i++) {
  setTimeout(function timer() {
    console.log(i);
  }, i * 1000);
}
```

first of all, because setTimeout is an asynchronous function, so the loop is executed first, at this time I it is 6, so a bunch of 6 will be output. There are three solutions:

the first method is to use closure

```js
for (var i = 1; i <= 5; i++) {
  (function (j) {
    setTimeout(function timer() {
      console.log(j);
    }, j * 1000);
  })(i);
}
```

In the above code, the immediate execution function is first used I the value is fixed to the parameter. j the above will not change, when the next execution timer this closure can use variables of external functions j to achieve the goal.

the second is to use setTimeout this parameter is considered timer the parameter of the function.

```js
for (var i = 1; i <= 5; i++) {
  setTimeout(
    function timer(j) {
      console.log(j);
    },
    i * 1000,
    i
  );
}
```

the third is to use let definition I to solve the problem, this is also the most recommend way

```js
for (let i = 1; i <= 5; i++) {
  setTimeout(function timer() {
    console.log(i);
  }, i * 1000);
}
```
