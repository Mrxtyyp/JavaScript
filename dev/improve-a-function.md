## improve-a-function

```js
let items = [
  {color: 'red', type: 'tv', age: 18},
  {color: 'silver', type: 'phone', age: 20},
  {color: 'blue', type: 'book', age: 17}
]

// an exclude array made of key value pair
const excludes = [
  {k: 'color', v: 'silver'},
  {k: 'type', v: 'tv'},
  ...
]

function excludeItems(items, excludes) {
  excludes.forEach( pair => {
    items = items.filter(item => item[pair.k] === item[pair.v])
  })

  return items
}
```

The function `excludeItems` need to filter `items` to get a result that don't have those key and value.
but, the above way is error.Ok. fine, let's implement it.
First, the key in `excludes` may be duplicate. we'd better use map to store those properties. For example:

```js
const excludes = [
  { k: "color", v: "silver" },
  { k: "type", v: "tv" },
  { k: "color", v: "red" },
];
const filter = {
  color: ["silver", "red"],
  type: ["tv"],
};
```

The map filter is final exclusion condition.And we're going to loop through the items array to ensure every item don't include those exclusion conditions.
Next, we're gonna implement the buildExclusionCondition function.

```js
function buildExclusionCondition(excludes) {
  const map = new Map();
  excludes.forEach((item) => {
    if (map.has(item.k)) {
      map.get(item.k).push(item.v);
    } else {
      map.set(item.k, [item.v]);
    }
  });
  return map;
}
```

Now, we need to filter out the qualified items.

```js
function excludeItems(items, excludes) {
  const exclusionCondition = buildExclusionCondition(excludes);

  return items.filter((item) => {
    return Object.keys(item).every(
      (i) =>
        !exclusionCondition.has(i) ||
        !exclusionCondition.get(i).includes(item[i])
    );
  });
}
```
