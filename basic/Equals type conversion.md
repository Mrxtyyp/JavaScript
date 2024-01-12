## what are the rules for type coersion of a equality oparator?

For a equality oparator, if the types of the compare of two sides are different, it will performed type conversion. if you compare whether x and y are the same:

1. First, it will determine whether the two sides are same, if so, comparing the size of both
2. If the two types are not same, it will do type conversion
3. It will first determine whether it is comparing null and undefined, if so, it will return true.
4. Determine whether the two types are string and number, if so, the string will converted to the number
5. Determine whether the one of both is boolean, if so, the boolean will be converted to the number and then do judge
6. Determine whether the one of both is object and the other is string or number or symbol, if so, the object will be converted to the raw type and then make a judgement.
