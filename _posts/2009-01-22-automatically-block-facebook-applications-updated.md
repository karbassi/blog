---

layout: post
title: "Automatically Block Facebook Applications Updated\!"
---

Two years later, I decided to take a look at my old, old, OLD Greasemonkey script to see if it was still working. This is after two minor updates on Facebook and one **major** update that changed the whole design and structure.

Surprisingly, the script works exactly like it should. I made one minor update, but after many tests, it works for me.

**If you have any suggestions, comments, or concerns, be sure to comment below.** If you find any situations where it doesn't work, please leave a comment and I will check it out.

**To use this script**, you need [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/748) add-on. Once you have it, just go here and click install: <http://userscripts.org/scripts/show/12393>.

Here's the code:

```javascript
// Auto-Block Facebook Apps
//
// Version 1.2
//
// Date Written: 2007-09-18
// Last Modified: 2009-01-22 02:18 PM (14:18)
//
// © Copyright 2007 Ali Karbassi.
// Released under the GPL license
// http://www.gnu.org/copyleft/gpl.html
//
// ——————————————————————————————————
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
// ——————————————————————————————————
//
// WHAT IT DOES:
// After the facebook profile page is loaded, it finds all the
// applications that your friends have invited you to and blocks them.
// Do not worry though, you can go to
// http://facebook.com/privacy.php?view=platform\&tab=all and unblock
// them
//
// NOTE: This does not alter, delete, edit, add, or anything else to
// your facebook profile. Just remove or disable this script and
// everything will be displayed the same as it used to
// ——————————————————————————————————
//
// UserScript
// `name        Auto-Block Facebook Apps 1.2
// `author Ali Karbassi
// `namespace   http://www.karbassi.com
// `description This script will block app invites sent to you by friends.
// After the facebook profile page is loaded, it finds all the
// applications that your friends have invited you to and blocks
// them. Do not worry though, you can go
// http://facebook.com/privacy.php?view=platform\&tab=all and
// unblock them.
// `include     http://*facebook.tld/home.php*
// `include http://\*facebook.tld/reqs.php\*
// /UserScript
// Find Subdomain
var subDomain = getSubDomain();

// Get links on the front page/request page
var anchors = document.getElementsByTagName('a');
var appReqExp = /reqs\\.php\#confirm*<span class="\d*"></span>*(.\*)/;

for (var i = 0; i \< anchors.length; i<span class="underline"></span>) {
if (appReqExp.exec(anchors\[i\].href)) {
prep(RegExp.$1, anchors\[i\]);
}
}

// Remove any notifications about apps.
removeNotifications();

// Functions
// PLEASE DO NOT TOUCH IF YOU HAVE NO IDEA WHAT YOU'RE DOING.
// YOU MIGHT BREAK IT.
// Prepares everything. When things are correct, it calls BlockApp.
function prep(appID, appNode) {
var postformMatch = /name="post\_form\_id" value="(\\w+)"/;
var post\_form\_id = 0;

GM\_xmlhttpRequest({
method: 'GET',
url: 'http://www.facebook.com/apps/block.php?id=' + appID
\+ '\&action=block',
headers: {
'User-Agent': window.navigator.userAgent,
'Accept': 'text/html',
},
onload: function(responseDetails) {
var searchString = 'This will not prevent you from seeing';
if( (responseDetails.status == 200)
&& (responseDetails.responseText.indexOf(searchString) \!= –1) ) {

// Show that we are working on it.
appNode.removeAttribute('href');
appNode.innerHTML = 'Reading confirmation page...';

postformMatch.exec(responseDetails.responseText);

// Calls function to block the app
BlockApp(RegExp.$1, appID, appNode);
}
}
});
}

function BlockApp(post\_form\_id, appID, appNode) {
GM\_xmlhttpRequest({
method: 'POST',
url: 'http://' + subDomain + 'facebook.com/apps/block.php?id=' + appID
\+ '\&action=block',
headers: {
'User-Agent': window.navigator.userAgent,
'Accept': 'text/xml',
'Content-Type': 'application/x-www-form-urlencoded',
},
data: 'post\_form\_id=' + post\_form\_id + '\&save=1',
onload: function(responseDetails) {
if (responseDetails.status == 200) {
appNode.innerHTML = 'App Blocked\!'
appNode.href = 'http://facebook.com/reqs.php';
}
},
onerror: function(responseDetails) {
appNode.removeAttribute('href');
appNode.innerHTML = 'App Block failed\!';
}
});
}

function removeNotifications() {
var inputs = document.getElementsByTagName('input');
for (var i = 0; i \< inputs.length; i<span class="underline"></span>) {
if (inputs\[i\].value  'Ignore') {
      for (var j = 0; j \< inputs\[i\].attributes.length; j++) {
        if ( (inputs\[i\].attributes\[j\].nodeName  'onclick') &&
(inputs\[i\].attributes\[j\].nodeValue.indexOf('click\_add\_platform\_app') \!= –1) ) {
var js = (inputs\[i\].attributes\[j\].nodeValue).split(' ');
js.shift();
js = js.join(' ');
location.href = 'javascript:' + js;
}
}
}
}
}

function getSubDomain() {
var subDomainRegExp = /http:\\/\\/(.\*\\.)facebook\\.com/;
var subDomain = '';
if (subDomainRegExp.exec(document.location) \!= 0) {
subDomain = RegExp.$1;
}
return subDomain;
}
```
