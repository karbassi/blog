---
layout: post
title: "Twitter style text counter in jQuery"
date: 2008-10-27
---

[![1]](http://www.flickr.com/photos/89943077@N00/2866119475/)

I. Love. jQuery. I can't say how much I love jQuery because some people might get jealous because jQuery might out-rank them in the scale of 0 to jAWESOME!

Enough drooling and leg humping. In a recent project, we needed a counter to display the number of characters the user had left in a text area. Nothing to hard or interesting. This sort of thing has been out there for years. The problem is, all the scripts I've found would automatically truncate the text. That is, if the user has 100 characters and they enter 105 characters, the 101 to 105th characters are gone. This is very annoying!

Rather than control the user and annoy them, we wanted to take the method Twitter does; Warn the user, don't allow them to submit until the warning is fixed. That is, if the text counter is negative, they cannot submit, but once it's 0 or greater, it's fair game.

To add to the fun, we needed visual cues, i.e. colours! After some search and no luck, I sat down and wrote this little beauty. **It's version 1 so be nice.**

You can always grab a from the [jQuery Plugin Repository].

```javascript
/*
 * twitterCounter
 *
 * Displays a counter with the remaining text.
 *
 * Example:
 *  $('#description').twitterCounter(
 *  {
 *     limit: 140,
 *     counter: '#textcounter',
 *
 *     okSize: 140,
 *     okStyle: '.ok',
 *
 *     watchSize: 20,
 *     watchStyle: '.watch',
 *
 *     warningSize: 10,
 *     warningStyle: '.warning',
 *
 *     errorSize: 0,
 *     errorStyle: '.error',
 *  });
 *
 * $Version: 2008-10-24
 * Copyright (c) 2008 Ali Karbassi
 * ali.karbassi@gmail.com
 */
jQuery.fn.twitterCounter = function(options) {
   var curSize = $(this).val().length;
   var charsLeft = options['limit'] - curSize;
   var types = ['ok', 'watch', 'warning', 'error'];
   var x = {};
   $.each(types,
   function() {
      var el = this.toString();
      x[el] = {
         'Max': options[el + 'Size'],
         'Style': options[el + 'Style'].substring(0, 1) == '.' || options[el + 'Style'].substring(0, 1) == '#' ? options[el + 'Style'].substring(1, options[el + 'Style'].length) : options[el + 'Style'],
         'Type': options[el + 'Style'].substring(0, 1) == '.' ? 'class': 'id'
      }
   });
   for (var i = 0; i < types.length; i++) {
      var el = types[i].toString(); // Last Element check
      if (i + 1 < types.length) {
         var nextEl = types[i + 1].toString();
         if (charsLeft > x[nextEl]['Max'] && charsLeft < x[el]['Max'] + 1) {
            clean();
         }
      } else {
         if (charsLeft < x[el]['Max']) {
            clean();
         }
      }
   }
   $(options['counter']).text(charsLeft); // Add an event so the counter updates when the user types.
   $(this).one('keyup',
   function() {
      $(this).twitterCounter(options);
   });
   function clean() {
      if (x[el]['Type'] == 'class') {
         $.each(types,
         function() {
            var temp = this.toString();
            if ($(options['counter']).hasClass(temp)) {
               $(options['counter']).removeClass(temp);
            }
         });
         $(options['counter']).addClass(x[el]['Style']);
      } else {
         $(options['counter']).id(x[el]['Style']);
      }
   }
};
```


[1]: http://tech.karbassi.com/images/posts/2008-10-27/punch.jpg "Punch Chart on Rapha&euml;l"
[jQuery Plugin Repository]: http://plugins.jquery.com/project/twittercounter
