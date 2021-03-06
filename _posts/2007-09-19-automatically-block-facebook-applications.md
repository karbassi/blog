---
layout: post
title: "Automatically Block Facebook Applications"
date: 2007-09-19
---

![Facebook Blocked Applications Header]

While working on the next version of my [Facebook Profile Cleaner], I noticed something that I was doing. Every time I would log into Facebook, I would have 3-5 new application invites. Personally, I don't care too much about them (if you didn't know already). I set out to see if I could come up with a way to automatically block them upon sign on/request.

That task seemed pretty easy, but it didn't turn out to be. First of all, Facebook hides their "Block Application" button on you. The first place you see it is on the application's page itself. Second, on the [user's request page]. it only shows an **add** and **ignore**. If you click ignore, it ignores that specific request, not any future ones. This gets real annoying when a ton of your friends decide to add (and send you requests) of the same application. And third, I was worried that maybe I would want to remove a block later. However Facebook was kind enough to provide a page to "remove" blocked applications. By going to [http://facebook.com/privacy.php?view=platform&tab=all], the second half of the page will list applications you have blocked. Notice they are listed by the order they were blocked; most recently blocked will be on the bottom.

![Facebook Blocked Applications]

That being said, I set out to actually **block** each application invite I get. After a few hours here and there, I finally got it fully working. The code should be clean enough for anyone interested enough to walk though. But note that if you just want the application and don't care for the actual code, then just install it and be on your merry way :).

**If you have any suggestions, comments, or concerns, be sure to comment below.**

**To use this script**, you need [Greasemonkey] add-on. Once you have it, just go here and click install: [http://userscripts.org/scripts/show/12393].

Here's the code:

```javascript
// Auto-Block Facebook Apps
//
// Version 1.0
//
// Date Written: 2007-09-18
// Last Modified: 2007-09-19 12:51 PM (12:51)
//
// (c) Copyright 2007 Ali Karbassi.
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
// select "Auto-Block Facebook Apps", and click Uninstall.
//
// --------------------------------------------------------------------
//
// WHAT IT DOES:
// After the facebook profile page is loaded, it finds all the
// applications that your friends have invited you to and blocks them.
// Do not worry though, you can go to
// http://facebook.com/privacy.php?view=platform&tab=all and unblock
// them
//
// NOTE: This does not alter, delete, edit, add, or anything else to
//       your facebook profile. Just remove or disable this script and
//       everything will be displayed the same as it used to
// --------------------------------------------------------------------
//
// ==UserScript==

// @name        Auto-Block Facebook Apps 1.0
// @author      Ali Karbassi
// @namespace   http://www.karbassi.com
// @description This script will block app invites sent to you by
// friends. After the facebook profile page is loaded, it finds all
// the applications that your friends have invited you to and blocks
// them. Do not worry though, you can go to
// http://facebook.com/privacy.php?view=platform&tab=all and
// unblock them.
// @include     http://facebook.com/home.php*
// @include     http://*.facebook.com/home.php*
// @include     http://facebook.com/reqs.php*
// @include     http://*.facebook.com/reqs.php*
// ==/UserScript==



// Find Subdomain
var subDomain = getSubDomain();

// Get links on the front page/request page
var anchors = document.getElementsByTagName('a');
var appReqExp = /reqs\.php#confirm_(\d*)_(.*)/;

for (var i = 0; i < anchors.length; i++) {
  if (appReqExp.exec(anchors[i].href)) {
    prep(RegExp.$1, anchors[i]);
  }
}

// Remove any notifications about apps.
removeNotifications();


// Functions
// PLEASE DO NOT TOUCH IF YOU HAVE NO IDEA WHAT YOU'RE DOING. YOU MIGHT BREAK IT.

// Prepares everything. When things are correct, it calls BlockApp.
function prep(appID, appNode) {
  var postformMatch = /name="post_form_id" value="(\w+)"/;
  var post_form_id = 0;

  GM_xmlhttpRequest({
    method: 'GET',
    url: 'http://www.facebook.com/apps/block.php?id=' + appID + '&action=block',
    headers: {
      'User-Agent': window.navigator.userAgent,
      'Accept': 'text/html',
    },
    onload: function(responseDetails) {
      if (
        (responseDetails.status == 200) &&
        (responseDetails.responseText.indexOf(
          'This will not prevent you from seeing'
        ) != -1)
      ) {
        // Show that we are working on it.
        appNode.removeAttribute('href');
        appNode.innerHTML = 'Reading confirmation page...';

        postformMatch.exec( responseDetails.responseText );

        // Calls function to block the app
        BlockApp(RegExp.$1, appID, appNode);
      }
    }
  });
}

function BlockApp(post_form_id, appID, appNode) {
  GM_xmlhttpRequest({
    method: 'POST',
    url: (
      'http://' + subDomain + 'facebook.com/apps/block.php?id=' +
      appID + '&action=block'
    ),
    headers: {
      'User-Agent': window.navigator.userAgent,
      'Accept': 'text/xml',
      'Content-Type': 'application/x-www-form-urlencoded',
    },
    data: 'post_form_id=' + post_form_id + '&save=1',
    onload: function (responseDetails) {
      if (
        (responseDetails.status == 200) &&
        (responseDetails.responseText.indexOf(
          'You have blocked this application'
        ) != -1)
      ) {
          appNode.innerHTML = 'App Blocked!'
          appNode.href = 'http://facebook.com/reqs.php';
        }
    },
    onerror: function (responseDetails) {
      appNode.removeAttribute('href');
      appNode.innerHTML = 'App Block failed!';
    }
  });
}

function removeNotifications() {
  var inputs = document.getElementsByTagName('input');
  for (var i = 0; i < inputs.length; i++) {
    if (inputs[i].value == 'Ignore') {
      for (var j = 0; j < inputs[i].attributes.length; j++) {
        if (
          (inputs[i].attributes[j].nodeName == 'onclick') &&
          (inputs[i].attributes[j].nodeValue.indexOf(
            'click_add_platform_app'
          ) != -1)
        ) {
          var js = (inputs[i].attributes[j].nodeValue).split(' ');
          js.shift();
          js = js.join(' ');
          location.href = 'javascript:' + js;
        }
      }
    }
  }
}

function getSubDomain() {
  var subDomainRegExp = /http:\/\/(.*\.)facebook\.com/;
  var subDomain = '';
  if (subDomainRegExp.exec(document.location) != 0) {
    subDomain = RegExp.$1;
  }
  return subDomain;
}
```

[Facebook Blocked Applications Header]: http://tech.karbassi.com/images/posts/2007-09-19/blocked.png
[Facebook Blocked Applications]: http://tech.karbassi.com/images/posts/2007-09-19/blocked2.png
[Facebook Profile Cleaner]: http://tech.karbassi.com/2007/08/27/facebook-profile-cleaner/
[user's request page]: http://facebook.com/reqs.php
[http://facebook.com/privacy.php?view=platform&tab=all]: http://facebook.com/privacy.php?view=platform&tab=all
[Greasemonkey]: https://addons.mozilla.org/en-US/firefox/addon/748
[http://userscripts.org/scripts/show/12393]: http://userscripts.org/scripts/show/12393
