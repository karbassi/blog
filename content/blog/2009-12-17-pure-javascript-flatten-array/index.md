---
title: "Pure JavaScript Flatten Array"
date: 2009-12-17
---

> **Update:** [Paul Irish] thought it would be grand to point out that my test case here isn’t the best. It’s good to note that the following functions work for all values in your array. I would suggest checking out the [QUnit testing page] to see other examples.

While working on my current project I needed a way to turn a heavily nested array and flatten it. There are some nice JavaScript libraries that have functions to do so, such as Underscore’s [_.flatten] and Prototype’s [.flatten] to name a few.

However, with [reduce] being implemented only in JavaScript 1.8 and not wanting to include a whole JavaScript library to do one task, I decided to write my own. You may want to take a look at the [QUnit testing page].

### Native Function

```javascript
function flatten(array) {
  var flat = []
  for (var i = 0, l = array.length; i < l; i++) {
    var type = Object.prototype.toString
      .call(array[i])
      .split(" ")
      .pop()
      .split("]")
      .shift()
      .toLowerCase()
    if (type) {
      flat = flat.concat(
        /^(array|collection|arguments|object)$/.test(type)
          ? flatten(array[i])
          : array[i]
      )
    }
  }
  return flat
}
```

Usage:

```javascript
var given = [[1, [2, [3, [4, [5, [6, [7, [8, [9, [0]]]]]]]]]]]
var value = flatten(given)

// 'value' => [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
```

### Array Object Extend:

```javascript
Array.prototype.flatten = function flatten() {
  var flat = []
  for (var i = 0, l = this.length; i < l; i++) {
    var type = Object.prototype.toString
      .call(this[i])
      .split(" ")
      .pop()
      .split("]")
      .shift()
      .toLowerCase()
    if (type) {
      flat = flat.concat(
        /^(array|collection|arguments|object)$/.test(type)
          ? flatten.call(this[i])
          : this[i]
      )
    }
  }
  return flat
}
```

Usage:

```javascript
var given = [[1, [2, [3, [4, [5, [6, [7, [8, [9, [0]]]]]]]]]]]
var value = given.flatten()

// 'value' => [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
```

[paul irish]: http://aurgasm.us/press/globe/BostonGlobe_Aurgasm_2005.07.31_pg1.jpg
[qunit testing page]: http://tech.karbassi.com/static/posts/2009-12-17/flatten-qunit.html
[_.flatten]: http://documentcloud.github.com/underscore/#flatten
[.flatten]: http://www.prototypejs.org/api/array/flatten
[reduce]: https://developer.mozilla.org/En/Core_JavaScript_1.5_Reference/Objects/Array/Reduce#Example.3a_Flatten_an_array_of_arrays
