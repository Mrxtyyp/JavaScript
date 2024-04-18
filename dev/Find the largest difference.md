## Find the largest difference

Requirements：
Given an array of numbers, pick any two numbers a and b, we could get the difference by Math.abs(a - b).

```js
largestDiff([-1, 2, 3, 10, 9]);
// 11,  obviously Math.abs(-1 - 10) is the largest

largestDiff([]);
// 0

largestDiff([1]);
// 0
```

We're going to implement a funciton called largestDiff to find the largest difference.
We create two variables are largest and smallest.And their initial value is the first item of the passed-in parameter.
If the length of passed-in parameter is 0, just return 0.
Let's loop through the passed-in parameter. Set the current item to the largest when the current item greater than the largest. Set the current item to the smallest when the current item less than the smallest.

```js
/**
 * @param {number[]} arr
 * @return {number}
 */
function largestDiff(arr) {
  if (arr.length === 0) return 0;
  let largest = arr[0],
    smallest = arr[0];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] > largest) {
      largest = arr[i];
    } else if (arr[i] < smallest) {
      smallest = arr[i];
    }
  }
  return Math.abs(smallest - largest);
}
```

Finally, we just make a subtraction and get the absolute value.
