---
title: "Object Type in Javascript"
date: 2009-12-18
---

Someone noted the interesting line that I use to find the object type.

```javascript
function getType(obj) {
  if (obj === undefined) {
    return "undefined"
  }
  if (obj === null) {
    return "null"
  }
  return Object.prototype.toString
    .call(obj)
    .split(" ")
    .pop()
    .split("]")
    .shift()
    .toLowerCase()
}

Object.prototype.getType = function () {
  return Object.prototype.toString
    .call(this)
    .split(" ")
    .pop()
    .split("]")
    .shift()
    .toLowerCase()
}
```

I posted the [QUnit test suite]. I’ve tested it in IE6-8, Safari 4, and Firefox 3.5.6. It would be greatly appreciated if you post your results.

While the typical method of using [typeof] or [instanceof] may produce results, they have their faults.

Douglas Crockford writes about [type detection] and his methods work for most cases, but not all.

On a side note, the reason why the `Object.prototype.getType` doesn't check for `undefined` or `null` is because neither of those have properties, that is, they are not an `Object`. That said, they cannot call any functions.

[qunit test suite]: http://tech.karbassi.com/static/posts/2009-12-18/type-detection-qunit.html
[typeof]: https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Operators/Special_Operators/typeof_Operator
[instanceof]: https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Operators/Special_Operators/instanceof_Operator
[type detection]: http://javascript.crockford.com/remedial.html
