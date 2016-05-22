# Solution: adding a list-of-links widget

(You can see source code and commits representing the steps for this solution in [a Git branch](https://github.com/apetro/angularjs-portal/tree/oa16-list-of-links-widget).)

## Locate the mock layout data

`/angularjs-portal-mock-portal/src/main/webapp/web/layoutDoc`

## Prepend an entry

Copy, paste, edit.

```
"layout":[
   {
     "nodeId": "-1",
     "title": "The Mysterious Bookshop",
     "description": "One of the oldest mystery specialist book stores in America, the Mysterious Bookshop is now in its 36th year. Previously located in midtown, the bookshop now calls Tribeca its home.",
     "url": "http://www.mysteriousbookshop.com/",
     "iconUrl": null,
     "faIcon": "fa-book",
     "fname": "mysterious-bookshop",
     "target": "_blank",
     "widgetURL": "",
     "widgetType":"list-of-links",
     "widgetConfig":{
        "launchText":"Go to bookstore",
        "links":[
           {
              "title":"Press",
              "href":"http://www.mysteriousbookshop.com/pages/mysterious-press",
              "icon":"fa-newspaper-o",
              "target":"_blank"
           },
           {
              "title":"Newsletter",
              "href":"http://www.mysteriousbookshop.com/pages/newsletter",
              "icon":"fa-envelope-o",
              "target":"_blank"
           },
           {
              "title":"Gift card",
              "href":"http://www.mysteriousbookshop.com/products/gift-card",
              "icon":"fa-credit-card",
              "target":"_blank"
           },
           {
              "title":"Events",
              "href":"http://www.mysteriousbookshop.com/pages/events",
              "icon":"fa-calendar-o",
              "target":"_blank"
           }
        ]
     },
     "widgetTemplate": null,
     "pithyStaticContent": null,
     "altMaxUrl": true,
     "renderOnWeb": false
     },
      {
         "nodeId":"u47l1n6",
         "title":"Email",
         ...
```

The `widgetType`, `widgetURL`, and `widgetConfig` are the salient bits.

## Build and run

``
mvn clean package && mvn jetty:run
```

## Enjoy the widget


![Mysterious bookshop widget](http://goo.gl/URtUz2)
