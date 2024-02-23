## what are the rules for type coersion of a equality oparator?

For a equality oparator, if the types of the compare of two sides are different, it will performed type conversion. if you compare whether x and y are the same:

1. First, it will determine whether the two sides are same, if so, comparing the size of both
2. If the two types are not same, it will do type conversion
3. It will first determine whether it is comparing null and undefined, if so, it will return true.
4. Determine whether the two types are string and number, if so, the string will converted to the number
5. Determine whether the one of both is boolean, if so, the boolean will be converted to the number and then do judge
6. Determine whether the one of both is object and the other is string or number or symbol, if so, the object will be converted to the raw type and then make a judgement.

## What are the conversion rules for other values to strings?

- For Null and Undefined types, null is converted to "null" and undefined is converted to "undefined".
- For Boolean types, true is converted to "true" and false is converted to "false".
- For Number types, the values are converted directly, but very small and very large numbers will be in exponential form.
- Symbol values are converted directly, but only explicit casts are allowed. Using implicit casts results in an error.
- For ordinary objects, unless toString() method is defined, Object.prototype.toString() will be called to return the value of the internal property [[Class]], such as "[object Object]". If the object has its own toString() method, it will be called when it is being stringified and then will use its return value.

## What are the rules for converting other values to numerical values?

- The value of Undefined is converted to NaN.
- Values of type Null are converted to 0.
- Boolean values of type, true converted to 1, false converted to 0.
- String value conversion is the same as using the Number() function, if it contains a non-numeric value, it is converted to NaN, and the empty string is 0.
- Values of type Symbol cannot be converted to numbers and will cause an error.
- Objects (including arrays) are first converted to the corresponding primitive type value, and if a non-numeric primitive type value is returned, it is then coerced to a number by following the rules above.

To convert a value to the corresponding primitive type value, the abstract operation ToPrimitive first checks (via the internal operation DefaultValue) whether the value has a valueOf() method. If it has and returns a primitive type value, cast it with that value. If not, the return value of toString(), if present, is used to cast.

If both valueOf() and toString() do not return primitive type values, a TypeError error will occur.

## What are the conversion rules for other values to Boolean values?

The following are false values:

1. undefined
2. null
3. false
4. +0
5. -0
6. NaN
7. ""

The result of the boolean coercion of a falsy value is false. Logically, anything other than a falsy value should be a truthy value.
