--- 
layout: post
title: Better array search
---
**Update:** Added more data to show differences.

During the journey of finding a better linear array search function in javascript, I decided to write my own. I decided to take a different approach. Here's the outcome.

{% highlight javascript %}
Array.prototype.small_search = function(search) {
    if (this[0] === search){ return 0; }
    var s = '\x00';
    var a = this.join(s);
    var b = a.search(search)-1;
    return a.substring(0, b).split(s).length;
};
{% endhighlight %}


With an array of less than 150 elements, it is much faster than Dustin Diaz's [in_array](http://www.dustindiaz.com/top-ten-javascript/) function. While they aren't the same, his can be adapted to return the index also.

The only downside with my function is that it becomes much slower after the array length is larger than 150 elements. So, if you have a small array, go ahead and use this, otherwise use Dustin's.

Times
-----

    Array Length: 5
    small_search: 0.020ms
    in_array:     0.098ms

    Array Length: 10
    small_search: 0.024ms
    in_array:     0.084ms

    Array Length: 50
    small_search: 0.042ms
    in_array:     0.095ms

    Array Length: 100
    small_search: 0.069ms
    in_array:     0.106ms

    Array Length: 150
    small_search: 0.087ms
    in_array:     0.111ms

    Array Length: 300
    small_search: 0.203ms
    in_array:     0.137ms

    Array Length: 500
    small_search: 0.418ms
    in_array:     0.132ms

    Array Length: 1000
    small_search: 0.813ms
    in_array:     0.138ms

    Array Length: 5000
    small_search: 3.530ms
    in_array:     0.312ms

    Array Length: 10000
    small_search: 6.718ms
    in_array:     0.441ms

Test it out on your own and come back with results.
