map-utils
========

util functions that tj commonly uses

## exists
### return true for any value other than ull or undefined
```js
var utils = require('tj-utils');

utils.exists(null);      // false
utils.exists(undefined); // false
utils.exists('foo');     // true
```

## pick
### returns a function which accepts an object and return a new object with the keys specified
### works with great with Array.map
```js
var utils = require('tj-utils');
var arr = [
  {
    foo: 1,
    bar: 1,
    qux: 1
  },
  {
    foo: 2,
    bar: 2,
    qux: 2
  }
];

arr.map(utils.pick('foo', 'bar'));
/*
  [
    {
      foo: 1,
      bar: 1
    },
    {
      foo: 2,
      bar: 2
    }
  ]
*/
```

## pluck
### returns a function which accepts an object and returns the value of the key specified
### works with great with Array.map
```js
var utils = require('tj-utils');
var arr = [
  {
    foo: 1,
    bar: 1,
    qux: 1
  },
  {
    foo: 2,
    bar: 2,
    qux: 2
  }
];

arr.map(utils.pick('foo', 'bar')); // [1, 2]
```

## set
### accepts obj or key val arguments and returns a function which accepts an object which those key/values will be set on
### works with great with Array.map
```js
var utils = require('tj-utils');
var arr1 = [
  {
    foo: 1,
    bar: 1
  },
  {
    foo: 2,
    bar: 1
  }
];
var arr2 = [
  {
    foo: 1
  },
  {
    foo: 2
  }
];

arr1.map(utils.set('qux', 1));
arr2.map(utils.set({ bar:1, qux:1 }));
/* both return:
  [
    {
      foo: 1,
      bar: 1,
      qux: 1
    },
    {
      foo: 2,
      bar: 1,
      qux: 1
    }
  ]
*/
```