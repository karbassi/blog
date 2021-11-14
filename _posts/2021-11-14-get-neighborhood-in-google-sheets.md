---
layout: post
title: 'Google Sheets: Get Neighborhood from Address or Query'
date: 2021-11-14
---

If you need you get the neighborhood based an address or location name, it's pretty easy using Google App Scripts and the [HERE API](https://developer.here.com/documentation). You'll need to supply your own HERE API key. They have a [freemium model](https://developer.here.com/pricing) that is pretty generious (_250k transactions per month_).

**First**, in your Google Spreadsheet, create an "Apps Script". As of 2021, you can do this by going to `Extentions` > `Apps Script`. Ths will open a new Apps Script file.

Inside the Apps Script site, rename the project to `getNeighborhood` and paste the following code inside `Code.gs`.

```js
const hereAPIKey = '<YOUR_HERE_API_KEY>';

function getNeighborhood(query) {
  query = query.trim();

  if (!query || !query.length) {
    throw new Error('<query> cannot be empty');
  }

  const encodedAddress = encodeURIComponent(query);
  const URL = `https://geocode.search.hereapi.com/v1/geocode?apiKey=${hereAPIKey}&q=${encodedAddress}`;
  const results = UrlFetchApp.fetch(URL);
  const data = JSON.parse(results);
  return data['items'][0]['address']['district'];
}
```

Be sure to save and click `Debug`. Confirm permissions once they pop up and you're set.

**Back inside your spreadsheet**, you can use the new function like so:

```js
=getNeighborhood("312 W Adams St, Chicago")
```

```js
=getNeighborhood("Sears Tower, Chicago")
```

```js
=getNeighborhood(A2)
```

**Source:** <https://github.com/karbassi/apps-script-getNeighborhood>
