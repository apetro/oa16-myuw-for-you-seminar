# Notifications in angularjs-portal

## What's a notification?

Notifications are succinct messages targeted to groups of users presented through the portal. They tend to be actionable, with an associated URL to launch to take action.

Notifications are about personally relevant things happening out in the world (rather than about features and functionality changes in the portal product).

### Anatomy of a notification

Notifications have:

```JSON
{
  "id"     : 2,
  "groups" : ["Users - Student SSN Update"],
  "title"  : "Our records indicate the Social Security Number in your Personal Information is invalid or missing. Please provide your Social Security Number or select to not provide your Social Security Number.",
  "actionURL" : "/portal/p/my-info-student-center-ssn.ctf1/max/action.uP?pP_action=loginAction",
  "actionAlt" : "UW-Madison Student Information",
  "dismissable" : true,
  "priority" : false
},
```

 * *id* : unique integer, used to track which notifications user has dismissed.
 * *groups* : the names of the uPortal groups in the audience of the notification.
 * *title* : text of the notification displayed in portal; preferably brief.
 * *actionURL* : relative or absolute URL that the text will link to, where the user can take action about the notification.
 * *actionAlt* : alt text associated with the action URL.
 * *dismissable* : true if the end user can dismiss the notification, false otherwise.
 * *priority* : true if the notification should be displayed with greater stridence; false otherwise.


## Ways notifications present

### Standard Notifications

Standard notifications contribute to the notification bell count. 

Clicking the bell takes the user to view applicable notifications.

### Priority Notifications

Priority notifications also contribute to the bell count and are directly presented in the header and the user can click to take action launching from the header.

When there are multiple applicable priority notifications, the header message abstracts to tell the user he or she has multiple available priority notifications, with the call to action to go look at notifications.

### Dismissable, or not

Notifications may be user-dismissable or not. User-dismissable tends to be appropriate when the portal cannot tell whether the notified-about situation is resolved.

For instance, suppose an adopter is considering notifying employees about an annual benefits enrollment opportunity.

If the nature of the target group is (static) "employees eligible for annual benefits enrollment", an adopter might make the notification user-dismissable so that once employees have exercised the opportunity, they can clear the notification to reduce their noise.

But if the nature of the target group is (dynamic) "employees eligible for annual benefits enrollment *who have not yet exercised that opportunity*", then the adopter might not make the notification user-dismissable, since the employee can effectively dismiss the notification by taking the indicated action.

## Configuring Notifications

Notifications are simply a JSON text file, at `/staticFeeds/notifications.json`. (This is present in `uw-frame`, and overridden in `angularjs-portal`).

Whether notifications display is governed by settings in `app-config.js` (in AngularJS-portal, overridden in `override.js`).

```json
.value('NOTIFICATION', {
    'enabled' : false,
    'groupFiltering' : false,
    'notificationFullURL' : 'notifications'
})
```

In `uw-frame` `2.3.0`, notifications are disabled by default. This is helpful for local development, but enabling these with the `notificationFullURL` pointed at the `angularjs-portal` `notifications.json` allows the frame-based app to participate in the portal notifications, that is, so that the user sees the same notifications "globally" whether in the landing page or in a frame-based app.

In `angularjs-portal` `4.2.1.6` notifications are enabled by default, and `groupFiltering` is turned on by default. 

### Filtering notifications by group

Localhost `angularjs-portal` uses a mock implementation of the groups web service to pretend that the mock user is a member of some groups.

In `override.js`, which overrides `uw-frame`'s `app-config.js`:

```
'SERVICE_LOC' : {
  ...
  'groupURL' : '/portal/api/groups',
```

In localhost development, that `/portal/api/groups` path is fulfilled by a text file,

`/angularjs-portal-mock-portal/src/main/webapp/api/groups`

## Limitations and potential in notifications

Of course, you could generate the `notifications.json` text file in any way you like, or even swap in a dynamic server-side program to provide the notifications data. From `uw-frame` and thus `angularjs-portal` 's perspective, it's just a path that returns some JSON.

UW-Madison has run up against the limitations in using a text file updated through the product deployment process, and so is considering options to make this more dynamic.

There may be room in the world for a great notifications management solution -- and so long as it produces JSON in the expected format, the `uw-frame` / `angularjs-portal` presentation technology would present those notifications.

The `groupFiltering` setting anticipates this. When that's set to `true`, `uw-frame` filters the notifications client-side, only showing those matching the user's groups. When that's set to false, `uw-frame` shows all the notifications returned, suitable  behavior if the `notifications.json` feed were dynamic, filtering the notifications for the user server-side.

Sooner, `uw-frame` notifications will likely change to encourage frame-based apps participating in displaying the portal-wide consistent notifications header.
