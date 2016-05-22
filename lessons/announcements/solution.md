# Solution: add a feature announcement

(You can see source code and commits representing the steps for this solution in [a Git branch](https://github.com/apetro/angularjs-portal/tree/oa16-announcements).)

## Find the announcements data

In `angularjs-portal`, it's in

`/src/main/webapp/staticFeeds/features.json`.

## Add an item

Copy, paste, edit.

```
{
    "id": 4,
    "title": "New Mysterious Bookstore widget",
    "description": "You can now conveniently access pages of the Mysterious Bookstore website from your portal home.",
    "img": "http://goo.gl/URtUz2",
    "learnMoreURL": "",
    "groups" : "All Users (PAGS)",
    "goLiveYear": 2016,
    "goLiveMonth": 1,
    "goLiveDay": 6,
    "isPopup" : false,
    "isBuckyAnnouncement" : true,
    "buckyAnnouncement" : {
      "shortTitle" : "Mysterious Widget",
      "shortDesc" : "A strange widget emerges from the mists...",
      "endDate": 2459486800000
    }
```
Take care with the commas: a comma separates this entry from the previous in the array, but there's no trailing comma at the end of the array.

Setting the `endDate` to an unreasonably high number ensures the feature item will not be suppressed by expiration.


## Build and run

`mvn clean package && mvn jetty:run`

## Take a look

![Bucky announces the widget](http://goo.gl/fTlSoJ)
