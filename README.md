# namecheapest

find the cheapest tlds on namecheap

https://freedns.afraid.org/subdomain/

If you just want a domain to use, try
https://freedns.afraid.org/

## Instructions

- go to [namecheap domains](https://www.namecheap.com/domains/new-tlds/explore)
- paste the following code into the devtools console:

```js
function sortOnKeys(dict) {
  var sorted = [];
  for (var key in dict) {
    sorted[sorted.length] = key;
  }
  sorted.sort();

  var tempDict = {};
  for (var i = 0; i < sorted.length; i++) {
    tempDict[sorted[i]] = dict[sorted[i]];
  }

  return tempDict;
}

let domainTables = document.querySelector(".gb-table");
let rows = domainTables.children[1];
let firstYrs = {};
let renewal = {};
for (let row of rows.children) {
  let name = row.querySelector(".gb-tld-name").innerText;
  let firstYr = row.querySelector(".gb-price").innerText;
  let renewalPrice = row.querySelector(".gb-price--special").innerText;
  firstYrs[name] = firstYr;
  renewal[name] = renewalPrice;
}

renewal = sortOnKeys(renewal);
firstYrs = sortOnKeys(firstYrs);
console.log("Cheapest first year prices:", firstYrs);
console.log("Cheapest renewal prices:", renewal);
```
