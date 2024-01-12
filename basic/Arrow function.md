## What happens If you create a new arrow function:

The arrow funciton is introduced in ES6. It does not have a prototype, nor does have its own this reference, and it cannot use the arguments parameter. So, it is not possible to used the new operater with an arrow function.

## The steps of implement a new function:

1. Create a new object
2. The new object's proto property point to the constructor fucntion's prototype property
3. Add attributes and functions to the new object
4. Return a new object

## The difference between arrow functions and the ordinary functions:

1. Arrow functions are simpler than ordinary functions
2. Arrow functions do not have their own 'this' keyword
3. This pointer inherited form the outer never change
4. Arrow functions cannot be used as constructors
5. Arrow functions do not have their own arguments
6. Arrow functions do not have a prototype
7. Arrow functions cannot be used to as Generator functions, and cannot be use the 'yield' keyword
