---
layout: post
title: Solution to The Spanner's "A bit of fun" challenge
date: 2007-10-25
---

A while back, [The Spanner]'s very own Gareth Heyes posted a [decent challenge]. As I stated in [a previous posting] I took on the challenge. It didn't take as long as I thought it would, but it was still challenging. I've waited a while before posting the actual code I used; that way people can figure it out themselves without any spoilers. That being said, it's about time I posted how I did it. Remember, my code might, and probably is, different than what you may have used.

**Note:** I use `console.debug`, which is from [Firebug] for [Firefox].

```javascript
var input = '38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 55 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 50 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 53 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 50 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 54 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 50 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 55 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 53 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 52 59 38 35 120 51 48 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 51 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 54 59 38 35 120 51 52 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 49 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 53 59 38 35 120 51 54 59 38 35 120 50 53 59 38 35 120 51 53 59 38 35 120 52 51 59 38 35 120 51 49 59 38 35 120 51 52 59 38 35 120 51 55 59';


String.prototype.ncr2c = function( )
{
  return this.replace( /&#x([\da-f]{2,4});/gi, function( $0, $1 ) { return String.fromCharCode( "0x" + $1 ) } )
}

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
}

// Split up string into array
var parts = input.split(' ');

// New parts
var step1 = Array();

// convert number into character code value
for( var i=0; i < parts.length; i++)
{
  step1[i] = String.fromCharCode(parseInt(parts[i]));
}

// Join all the values together
step1 = step1.join('');
console.debug("step1: %o", step1);

// Split again at the ';' point
var step2 = step1.split(';');

// Pointless empty element at the end.
step2.pop();

// We still need the ';' at the end of each element
for( var i=0; i < step2.length; i++)
{
  step2[i] += ';';
  step2[i] = step2[i].ncr2c();
}

// Join all the values together, again.
step2 = step2.join('');
console.debug("step2: %o", step2);

// Split again by '%' point
var step3 = step2.split('%5C');

// Pointless element in the beginning
step3.shift();

console.debug("step3: %o", step3);

var step4 = Array();

// convert number into character code value
for( var x=0; x < step3.length; x++)
{
  step4[x] = step3[x].octToAscii();
}

// Our Answer
console.debug("step4: %o", step4.join(''));
```

Hope this helps someone out there.

[The Spanner]: http://www.thespanner.co.uk/
[decent challenge]: http://www.thespanner.co.uk/2007/10/10/a-bit-of-fun/
[a previous posting]: http://tech.karbassi.com/2007/10/10/javascript-octal-to-ascii/
[Firebug]: http://www.getfirebug.com/
[Firefox]: http://www.mozilla.com/en-US/firefox/
