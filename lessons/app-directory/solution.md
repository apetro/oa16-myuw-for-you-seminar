# Solution: tweaking the mock app directory data

(You can see source code and commits representing the steps for this solution in [a Git branch](https://github.com/apetro/angularjs-portal/tree/oa16-app-directory).)

## Find the file

`/angularjs-portal-mock-portal/src/main/webapp/web/marketplace/entries.json` .

## Find an entry suitable for editing

Let's work with the very first entry.

```JSON
{
  "canAdd": true,
  "layoutObject": {
    "nodeId": "-1",
    "title": "Wiscard Balance",
    "description": "See your wiscard balance, make a deposit, or request money.",
    "url": "https://online.wiscard.wisc.edu/login.php?cid=120",
    "iconUrl": null,
    "faIcon": "fa-credit-card-alt",
    "fname": "wiscard-balance",
    "target": "_blank",
    "widgetURL": "/web/api/wiscard",
    "widgetType": "generic",
    "widgetTemplate": "\n          <div class='widget-body'>\n            <loading-gif data-object='content' data-empty='isEmpty'></loading-gif>\n            <div ng-if=\"content && (content.data | filter: account=103).length > 0\"  class='center' style='padding:20px;'>\n              <span style='font-size: 35px; color:#b70101'> {{ (content.data | filter: account=103)[0].balance | currency:\"$\":2}}</span>\n            </div>\n            <div ng-if='isEmpty' style='padding: 20px; font-size: 14px;'>\n              <i class='fa fa-exclamation-triangle fa-3x pull-left' style='color: #b70101;'></i>\n              <span>Balance unavailable, please try again later</span>\n            </div>\n            <div class=\"center\">\n              <i class=\"fa fa-credit-card-alt fa-5x\" style=\"color: #cbcbcb;\"></i>\n            </div>\n          </div>\n          <a class='btn btn-default launch-app-button' href='https://online.wiscard.wisc.edu/login.php?cid=120'>Manage my Wiscard</a>\n        ",
    "widgetConfig": {
      "evalString": "!$scope.content.data || ($scope.content.data | filter: account=103).length  === 0"
    },
    "staticContent": "\n        \n          <a href=\"https://online.wiscard.wisc.edu/login.php?cid=120\">Access your Wiscard account.</a>\n        \n      ",
    "pithyStaticContent": null,
    "altMaxUrl": true,
    "renderOnWeb": false
    },
  "fname": "wiscard-balance",
  "lifecycleState": "PUBLISHED",
  "rating": 0,
  "relatedPortlets": [],
  "renderUrl": "https://online.wiscard.wisc.edu/login.php?cid=120",
  "portletWebAppName": "/SimpleContentPortlet",
  "faIcon": "fa-credit-card-alt",
  "maxUrl": "https://online.wiscard.wisc.edu/login.php?cid=120",
  "portletReleaseNotes": {},
  "shortUrl": null,
  "userRated": 0,
  "marketplaceScreenshots": [],
  "title": "Wiscard Balance",
  "portletName": "cms",
  "categories": [],
  "keywords": [],
  "description": "See your wiscard balance, make a deposit, or request money.",
  "name": "Wiscard Balance",
  "id": "5996",
  "type": "Portlet",
  "target": "_blank"
},
```

## Edit it

The exercise is to see how we can change the data.

So, let's make up an entry for Otto Penzler's bootstore, just for fun.

```JSON
{
  "canAdd": true,
  "layoutObject": {
    "nodeId": "-1",
    "title": "The Mysterious Bookshop",
    "description": "One of the oldest mystery specialist book stores in America, the Mysterious Bookshop is now in its 36th year. Previously located in midtown, the bookshop now calls Tribeca its home.",
    "url": "http://www.mysteriousbookshop.com/",
    "iconUrl": null,
    "faIcon": "fa-book",
    "fname": "mysterious-bookshop",
    "target": "_blank",
    "widgetURL": "/web/api/wiscard",
    "widgetType": "generic",
    "widgetTemplate": "\n          <div class='widget-body'>\n            
    <p>Widget</p>
    </div>\n          <a class='btn btn-default launch-app-button' href='http://www.mysteriousbookshop.com/'>Go to bookstore</a>\n        ",
    "staticContent": "\n        \n          <a href=\"http://www.mysteriousbookshop.com/\">Go to bookstore.</a>\n        \n      ",
    "pithyStaticContent": null,
    "altMaxUrl": true,
    "renderOnWeb": false
    },
  "fname": "mysterious-bookshop",
  "lifecycleState": "PUBLISHED",
  "rating": 5,
  "relatedPortlets": [],
  "renderUrl": "http://www.mysteriousbookshop.com/",
  "portletWebAppName": "/SimpleContentPortlet",
  "faIcon": "fa-book",
  "maxUrl": "http://www.mysteriousbookshop.com/",
  "portletReleaseNotes": {},
  "shortUrl": null,
  "userRated": 0,
  "marketplaceScreenshots": [],
  "title": "Mysterious Bookshop",
  "portletName": "cms",
  "categories": [],
  "keywords": ["murder"],
  "description": "One of the oldest mystery specialist book stores in America, the Mysterious Bookshop is now in its 36th year. Previously located in midtown, the bookshop now calls Tribeca its home.",
  "name": "Mysterious Bookshop",
  "id": "5996",
  "type": "Portlet",
  "target": "_blank"
},
```

## Build and run

`mvn clean package && mvn jetty:run`

## Try it out in a web browser

http://localhost:8080

Click the Add more to home button to get to the app directory.

![Getting to the app directory](http://goo.gl/A7g7Ue)

This edited entry is displayed first.

![App directory entry for Mysterious Bookshop](http://goo.gl/9ehkUR)

## Not seeing it? Try clearing your cache

You can easily clear your browser cache of `angularjs-portal` content at

http://localhost:8080/web/settings

via the controls in the "Danger Zone", which are not at all dangerous. `angularjs-portal` gracefully re-loads whatever it can't find in local storage.

![Tool for clearing cache](http://goo.gl/pdDItb)
