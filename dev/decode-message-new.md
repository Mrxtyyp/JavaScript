## decode-message-new

To implement a algorithm that can decode message from a 2-D array.

```js
// 2-D array
[
  ["I", "B", "C", "A", "L", "K", "A"],
  ["D", "R", "F", "C", "A", "E", "A"],
  ["G", "H", "O", "E", "L", "A", "D"],
];
```

The rules as follow:

[0,0] — [1,1] — [2,2] — [1,3] — [0,4] — [1,5] — [2,6]

The number of rows is increasing
The number of cols is among 0 to 3 alternately
So, the number 2 point is key.

First, we do a format check. it’s return empty string if the format is fail.

And then, we need three variable to store value, they are str, point, flag, where str is used to store every string.the point is the current number of col, the flag is a alternate flag.

The most important is check out the flag, from 2 to 0, form 0 to 2.

```js
/**
 * @param {string[][]} message
 * @return {string}
 */
function decode(message) {
  if (message.length === 0 || message[0].length === 0) return "";
  let str = "",
    point = 0,
    flag = 1;
  const row = message[0].length;
  const col = message.length;
  for (let i = 0; i < row; i++) {
    str += message[point][i];
    point = point + flag;
    if (point == col - 1 || point == 0) {
      flag = -flag;
    }
  }
  return str;
}
```
