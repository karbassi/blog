---
layout: post
title: "Facebook Profile Cleaner"
date: 2007-08-27
---

I use [Facebook] the way you should; for keeping track of my friends, their information, planning events, discussing things, etc. I don't believe that Facebook should be another [MySpace] (a popularity contest).

That being aside, I didn't enjoy the fact that Facebook now allows "apps" (applications/widgets) to be added to profiles. Sure, some applications are useful, but like MySpace, it gets annoying. So, with that I created a [Greasemonkey] script to remove, per se, all those apps. You can also specify others, such as "Mini-Feed", "Education", etc.

**To use this script**, you need [Greasemonkey] add-on. Once you have it, just go here and click install: [http://userscripts.org/scripts/show/11747].

I spent around 1 hour and whipped it up and it works better wonders. To me, it loads the page faster. Here's the code:

```javascript
// Facebook Profile Cleaner
//
// Version 1.0
//
// Date Written: 2007-08-26
//
// Copyright (c) 2007, Ali Karbassi
// Released under the GPL license
// http://www.gnu.org/copyleft/gpl.html
//
// --------------------------------------------------------------------
//
// This is a Greasemonkey user script.
//
// To install, you need Greasemonkey: http://greasemonkey.mozdev.org/
// Then restart Firefox and revisit this script.
// Under Tools, there will be a new menu item to "Install User Script".
// Accept the default configuration and install.
//
// To uninstall, go to Tools/Manage User Scripts,
// select "Facebook Profile Cleaner", and click Uninstall.
//
// --------------------------------------------------------------------
//
// WHAT IT DOES:
// After the facebook profile page is loaded, it finds all the
// applications that are not in the list below and 'removes' them. By
// remove, I mean, not display them.
//
// NOTE: This does not alter, delete, edit, add, or anything else to
//       your facebook profile. Just remove or disable this script and
//       everything will be displayed the same as it used to
// --------------------------------------------------------------------
//
// ==UserScript==
// @name           Facebook Profile Cleaner
// @namespace      http://tech.karbassi.com/
// @description    Removes applications from all profiles. Clean out
//                 all those annoying applications people add. This
//                 script will remove all the applications (plus
//                 others if specified) from any facebook profile
//                 you view.
// @include        http://*.facebook.com/*
// ==/UserScript==

// Comment out the ones you don't want displayed
// Note: This list is the 'original' apps
var AppsToKeep = [
    'box_app_2407511955',   // Mutual Friends
    'box_app_2356318349',   // Local Network Friends
    //'box_app_2503140832', // Friends in Other Networks
    'box_app_2305272732',   // Photos
    //'box_app_2347471856', // Notes
    //'box_app_2361831622', // Groups
    //'box_app_2341989679', // Mini-Feed
    'box_app_2327158227',   // Information
    'box_app_2297529396',   // Education and Work
    //'box_app_2386512837', // Gifts
    'box_app_2719290516',   // The Wall
];


// DO NOT EDIT
// Well, unless you know what you're doing

Array.prototype.inArray = function (value) {
    var i = this.length;
    while (i--) {
        if (this[i] === value) {
            return true;
        }
    }
    return false;
};

pageDivs = document.getElementsByTagName('div');

// Delete application divs
for (var i = 0; i < pageDivs.length; i++) {
    if (
        (pageDivs[i].id.indexOf('box_app_') === 0) &&
        (!AppsToKeep.inArray(pageDivs[i].id))
    ) {
        pageDivs[i].style.display = 'none';
    }
}
```

[Facebook]: http://www.facebook.com
[MySpace]: http://www.myspace.com
[Greasemonkey]: https://addons.mozilla.org/en-US/firefox/addon/748
[http://userscripts.org/scripts/show/11747]: http://userscripts.org/scripts/show/11747
