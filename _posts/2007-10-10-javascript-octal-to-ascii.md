---
layout: post
title: "Javascript: Octal to ASCII"
date: 2007-10-10
---

Gareth Heyes posted a [fun little challenge] and I couldn't help but attack it. It took me longer than I thought. Not to be a spoiler, but at some point you have to convert octals to <abbr title="American Standard Code for Information Interchange">ASCII</abbr> values. Now, I have done decimal to ASCII, binary to ASCII, and even hex to ASCII, but never octal to ASCII. Searching around, I found everyone seemed to use PHP, <abbr title="Active Server Pages">ASP</abbr>, or some sort of "higher" level programming.

I found some really old code on some google cache, which I lost the url to, and it seemed to work. By working, I mean, the idea was right, the code wasn't. After fooling around with it for a bit, I got something like the following.

```javascript
String.prototype.octToAscii = function()
{
  var temp = '', result = '', input = this + '%';
  for(i = 0; i = 0; j++, k--)
      {
        if( (temp.match("\\n")) && (notMatchedYet) )
        {
          k--;
          notMatchedYet = false;
        }
        partial = temp.charAt(j) * Math.pow(8, k);
        running += partial;
      }
      result += String.fromCharCode(running);
      temp = '';
    }
  }
  return result.replace(/%40%/g, "%40<br />%")
};
```

Gareth posted his answer as follows, but I cleaned up the styling a little to be more readable.

```javascript
c = '38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 55 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 50 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 53 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 50 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 54 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 50 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 55 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 53 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 54 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 55 59';

c = c.split(' ');
d = '';

for(i = 0; i < c.length; i++)
    d += String.fromCharCode(c[i]);

c = d.replace(/&#x/g,'');
c = c.split(';');
d = '';

for(i = 0; i < c.length; i++)
    d += String.fromCharCode(parseInt(c[i],16));

c = unescape(d).split('\\');
d='';

for(i = 1; i < c.length; i++)
    d += String.fromCharCode(parseInt(c[i],8));

alert(d);
```

> **2018 update**: Just for fun.

```javascript
function octToAscii(str) {

  // Base 10
  str = str
    .split(' ')
    .map(function(c) { return String.fromCharCode(parseInt(c, 10)); })
    .join('');

  // Base 16
  str = str.replace(/&#x/g, '')
    .split(';')
    .map(function(c) { return String.fromCharCode(parseInt(c, 16)); })
    .join('');

  // Base 8
  str = unescape(str)
    .split('\\')
    .map(function(c) { return String.fromCharCode(parseInt(c, 8)); })
    .join('');

  return str;
};

console.log( octToAscii(c) );
```

[fun little challenge]: http://www.thespanner.co.uk/2007/10/10/a-bit-of-fun/
