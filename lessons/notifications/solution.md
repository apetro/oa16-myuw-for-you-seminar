# Solution to adding and turning on notifications

## Adding a notification to angularjs-portal

(You can see source code and commits representing the steps for this solution in [a Git branch](https://github.com/apetro/angularjs-portal/tree/oa16-notifications).)

### Add the notification

In `angularjs-portal` `/angularjs-portal-home/src/main/webapp/staticFeeds/notifications.json`:

add another notification:

```json
,
      {
        "id"     : 10,
        "groups" : ["All Users (PAGS)"],
        "title"  : "Lunch is not provided.",
        "actionURL" : "https://docs.google.com/document/d/1wgZD0NxjXHC4QWUZFFOaxbwLxqmNeaQpIDH9OZNcvgU/edit",
        "actionAlt" : "Lunch options",
        "priority": true
      }
```

Be sure to get the commas right: comma before the new entry (so, between entries), but no comma after (that is, final item in array is not followed by a comma).


### Run it

First use `control-C` to stop Jetty running AngularJS-portal if it was already running.

Then, `mvn clean package && mvn jetty:run` in a terminal in the root of `angularjs-portal`.

### Take a look in a browser

Header reflects multiple priority notifications:

![Header indicates two priority notifications](http://goo.gl/Q4TR4z)

Notifications page displays them:

![Showing the additional notification](http://goo.gl/4is1eO)

## Turning on and adding a notification to uw-frame

(You can see source code and commits representing the steps for this solution in [a Git branch](https://github.com/apetro/uw-frame/tree/oa16-notifications).)

### Configure frame to use notifications

Customize `uw-frame` `/uw-frame-components/js/app-config.js` to turn on notifications, by setting `NOTIFICATION` --> `enabled` to `true`.

```JavaScript
.value('NOTIFICATION', {
            'enabled' : true,
            'groupFiltering' : false,
            'notificationFullURL' : 'notifications'
        })
```
Note: that `notificationsFullURL` is the URL of the notifications page, not the URL of the notifications JSON feed.

(You could turn on `groupFiltering`, but then you'd have to configure getting the right groups from a mock groups JSON feed file, so it'd be more complexity and configuration.)

### Configure frame to use the sample notifications

Customize `uw-frame` `/uw-frame-components/js/app-config.js` to set `SERVICE_LOC` --> `notificationsURL` to point at the sample notifications JSON file rather than the empty default file.

```JavaScript
.value('SERVICE_LOC', {
          'aboutURL' : null,
          'sessionInfo' : 'staticFeeds/session.json',
          'notificationsURL' : 'staticFeeds/sample_notifications.json',
```

(You could instead use the default or a different JSON file, but then you'd have to edit that file to include example notifications.)

### Run it

In a terminal in the root directory of `uw-frame`, run `npm run static`.

That should churn for a while and then yield

```
Superstatic started.
Visit http://localhost:3474 to view your app.
```

### Take a look in a browser

Take a look in a web browser at http://localhost:3474 .

![Notifications turned on](http://goo.gl/CtyXY3)
