# Exercise: Add a notification

## Task 1: Add a notification in `angularjs-portal`

`angularjs-portal` is displaying some notifications out of the box, so this task is a matter of adding an item to its sample data.

Hints:

* Recall it's `mvn clean package && mvn jetty:run` in a terminal at the root of AngularJS-portal to build and run it, and `control-C` in that terminal to stop it.
* Target the notification to the group `All Users (PAGS)` since the mock groups JSON feed reports the mock demo user as a member of this group.


## Task 2: Turn on notifications and add a notification in `uw-frame`

A frame-based app might turn on notifications to participate in portal-wide notifications.

When developing an app for real, you'd be doing this in a Maven overlay for that app, setting it in `override.js`. The way `angularjs-portal` itself does exactly this is a good analog.

But for purposes of understanding how this configuration work, in this exercise, turn on and add at least one notification in `uw-frame` itself.

Hints:

* Recall it's `npm run static` in a terminal at the the root of `uw-frame` to build and run it once you've configured this, and `control-C` in that terminal to stop it.
* You'll need to turn on notifications in `app-config.js`
* Leave groupFiltering turned off, for demo purposes. (If it's turned on you'd need to also tweak the mock groups web service response to put the example user into relevant groups.)
* While the shipping `notifications.json` contains no notifications, there's a sample file shipped next to it.
