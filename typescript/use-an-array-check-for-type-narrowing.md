# Use An Array Check For Type Narrowing

You're creating a concatenation function, for melding two values together in a single array, with the following function signature:

```javascript
type ConcatFunction = (value: any | any[], array: any[]) => any[];
```

The first value might be a single entry, or it might be an entire array. Both cases need to be handled. Using `Array.isArray` as a _type guard_, you can differentiate between the two cases like so:

```javascript
const concat: ConcatFunction = (value, array) => {
  if (Array.isArray(value)) {
    return [...value, ...array];
  } else {
    return [value, ...array];
  }
};

concat(true, [1, 2, 3]);
// [true, 1, 2, 3]

concat([1, 2, 3], ["a", "b", "c"]);
// [1, 2, 3, 'a', 'b', 'c']
```

This is known as [type narrowing](https://www.typescriptlang.org/docs/handbook/2/narrowing.html). Type narrowing basically means moving from less precise types to more precise types.