## What is the understanding of class array objects?

An object with the length attribute and several Index attributes can be called a class array object. Class array objects are similar to arrays, but array methods cannot be called. Common class array objects include arguments and DOM methods. Function parameters can also be considered as class array objects because they contain the length attribute value, which represents the number of parameters that can be received.

## There are several common methods to convert class arrays into arrays:

Array.prototype.slice.call(arrayLike)
Array.prototype.splice.call(arrayLike, 0)
Array.prototype.concat.apply([], arrayLike)
Array.from(arrayLike)
