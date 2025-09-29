## Statistics Calculator
This is a calculator that can calculate the count, mean, median, range, mode, variance and staandard deviation of a data separated by commas.
The thought process is that every thing the calculator does has a function, so range has a function, mode has a function etc.

### Count Function

```js
const getCount = (array) => array.length;

```
`array.length` gives the number of elements in the array.

### Mean Function
```js
const getMean = (array) =>
  array.reduce((acc, el) => acc + el, 0) / array.length;

```

- array.reduce((acc, el) => acc + el, 0)

- reduce walks the array and combines its items into a single value (here, the sum).

- ((acc, el) => acc + el) is the reducer callback:

- acc = accumulator (the running result).

- el = current element from the array.

- For each element: return acc + el which becomes the next acc.

- 0 at the end is the initial value for acc (so the first step adds the first element to 0).
- / array.length
- After reduce gives the total sum, you divide by the number of elements to get the mean (average)

### Median Function
```js
const getMedian = (array) => {
  const sorted = array.toSorted((a, b) => a - b);

// array.toSorted(...)

// toSorted is a new JavaScript method (ES2023).

// It works like array.sort(...), but instead of changing the original array, it creates a new sorted copy.

// This means:

// array stays the same.

// sorted becomes a new array with elements sorted.

//(a, b) => a - b

// This is the comparator function for sorting numbers.

// If a - b < 0, then a comes before b.

// If a - b > 0, then b comes before a.

// If a - b === 0, they’re considered equal.
  const median =
    sorted.length % 2 === 0
      ? getMean([sorted[sorted.length / 2], sorted[sorted.length / 2 - 1]])
      : sorted[Math.floor(sorted.length / 2)];

// If array length is even → take the middle two values, find their mean.

// If array length is odd → pick the exact middle value.

 return median;
};

```

