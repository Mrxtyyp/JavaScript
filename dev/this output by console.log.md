## What does the code snippet to the right output by console.log?

The today practice is find the right output depend on a object called obj, the obj as follow:

```js
const obj = {
  a: 1,
  b: function () {
    console.log(this.a);
  },
  c() {
    console.log(this.a);
  },
  d: () => {
    console.log(this.a);
  },
  e: (function () {
    return () => {
      console.log(this.a);
    };
  })(),
  f: function () {
    return () => {
      console.log(this.a);
    };
  },
};

console.log(obj.a);
obj.b();
obj.b();
const b = obj.b;
b();
obj.b.apply({ a: 2 });
obj.c();
obj.d();
obj.d();
obj.d.apply({ a: 2 });
obj.e();
obj.e();
obj.e.call({ a: 2 });
obj.f()();
obj.f()();
obj.f().call({ a: 2 });
```

And we're gonna find the output of each snippet code:

1. `console.log(obj.a)` It's easy, that is 1.
2. `obj.b()` b is function, so its this depends on who the function is called, here it's called through obj, so, this is point to obj, the output is 1.
3. `;(obj.b)()` The way of writing actually is same to the previous way. so the output also is 1.
4. `const b = obj.b; b()` There is use a variable b to save `obj.b`, then call b(); At the second point we said that its this depends on who the function is called. So, actullay the b is attached to `window`, finally, we can guess that its output is undefind.
5. `obj.b.apply({a: 2})` This obj.bfunction is called by applymethod, so the this keyword within obj.bshould be point to {a: 2}. so the output is 2.
6. `obj.c()`This way is a shorthand for c: function() {console.log(this.a)}. so the output also is 1.
7. `obj.d()` It's the property of implementation using arrow function. so the inner this will be window. so that is undefind.
8. `;(obj.d)()` This way is same to the previous way. so that is undefind.
9. `obj.d.apply({a:2})` The point of this cannot be changed. so that yet is undefind.
10. `obj.e()`there is a immediate function. it is equal to obj.d. so log out undefind.
11. `;(obj.e)()`Similar to the above.
12. `obj.e.call({a:2})` Similar to the numer 9 point.
13. `obj.f()()` The this pointor of the arrow function will be inherited form the top level function.so, the this pointer actually is obj.it is 1.
14. `;(obj.f())()` `obj.f().call({a:2})` Similar to the above.
