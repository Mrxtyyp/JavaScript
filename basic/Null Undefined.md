## The difference of Null and Undefind:

First，Null and Undefined are both basic data types. These data types has only one value.which is null and undefined.

Undefined means undefined, Null means empty object. When general variables is declared and not defined, it will return undefined. Null is mainly to assign to some variables that may return object as initialization.

Undefined is not a reserved word in JavaScript. It means that can be used as a variable name, but it's very dangerous, It will affect the judgment of undefined value. We can through some methods to get safely undefined values, such as void 0.

When using typeof to judgment of these two types. Null typing will return "object", which is a historical problem. When using a double equal sign to compare these two types, it will return true, and return false when using a triple equal sign.
