---
layout: post
title: "Javascript: ucfirst"
date: 2007-10-08
---

In [PHP] there is [ucfirst] whose purpose is to uppercase the first letter of the string. While working in Javascript I ran into a problem where I wanted to do this. I searched high and low and couldn't find a native function that would do this. So, I ended up writing my own.

```javascript
String.prototype.ucfirst = function () {

    // Split the string into words if string contains multiple words.
    var x = this.split(/\s+/g);

    for (var i = 0; i < x.length; i++) {

        // Splits the word into two parts. One part being the first
        // letter, and second being the rest of the word.
        var parts = x[i].match(/(\w)(\w*)/);

        // Put it back together but uppercase the first letter and
        // lowercase the rest of the word.
        x[i] = parts[1].toUpperCase() + parts[2].toLowerCase();
    }

    // Rejoin the string and return.
    return x.join(' ');
};
```

A quick example on how to use it:

```javascript
var s = "hello my name is ali karbassi.";

//hello my name is ali karbassi.
document.write( s );

//HELLO MY NAME IS ALI KARBASSI.
document.write( s.toUpperCase() );

//hello my name is ali karbassi.
document.write( s.toLowerCase() );

//Hello My Name Is Ali Karbassi
document.write( s.ucfirst() );
```

**Update:** [Adam] noted another way to do this.

```javascript
str = str.toLowerCase().replace(/\b([a-z])/gi,function(c){return c.toUpperCase()});
```

[PHP]: http://www.php.net
[Adam]: http://tech.karbassi.com/2007/10/08/javascript-ucfirst/?dsq=8795098#comment-8795098
[ucfirst]: http://us.php.net/ucfirst
