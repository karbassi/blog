---
layout: post
title: "Better array search"
date: 2009-07-21
---

During the journey of finding a better linear array search function in javascript, I decided to write my own. I decided to take a different approach. Here's the outcome.

```javascript
Array.prototype.small_search = function(search) {
    if (this[0] === search){ return 0; }
    var s = '\x00';
    var a = this.join(s);
    var b = a.search(search)-1;
    return a.substring(0, b).split(s).length;
};
```

With an array of less than 150 elements, it is much faster than Dustin Diaz's [in_array] function. While they aren't the same, his can be adapted to return the index also.

The only downside with my function is that it becomes much slower after the array length is larger than 150 elements. So, if you have a small array, go ahead and use this, otherwise use Dustin's.

### Times

| Array Length | small_search | in_array    |
|--------------|--------------|-------------|
| 5            | **0.020ms**  | 0.098ms     |
| 10           | **0.024ms**  | 0.084ms     |
| 50           | **0.042ms**  | 0.095ms     |
| 100          | **0.069ms**  | 0.106ms     |
| 150          | **0.087ms**  | 0.111ms     |
| 300          | 0.203ms      | **0.137ms** |
| 500          | 0.418ms      | **0.132ms** |
| 1000         | 0.813ms      | **0.138ms** |
| 5000         | 3.530ms      | **0.312ms** |
| 10000        | 6.718ms      | **0.441ms** |

Test it out on your own and come back with results.

[in_array]: http://www.dustindiaz.com/top-ten-javascript/
