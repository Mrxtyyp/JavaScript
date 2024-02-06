## What is the result of typeof NaN?

NaN stands for "not a number". It is a "sentinel value" used to indicate an error condition in the number type, specifically the result of a failed math operation.

```js
typeof NaN; // "number"
```

NaN is a special value that is not equal to itself and is the only non-lexive (reflexive, that is, x === x does not hold) value. And NaN! == NaN is true.
