## Can the properties of const objects be modified?

const guarantees not that the value of a variable cannot be changed, but that the memory address to which the variable points cannot be changed.

For basic data types (numbers, strings, boolean values), their values are stored at the memory address the variable points to, so it is equivalent to a constant.

But for data of reference type (mainly objects and arrays), the variable points to the memory address of the data, saving only a pointer, const can only guarantee that the pointer is fixed, as it points to the data structure is not mutable, it can not control.
