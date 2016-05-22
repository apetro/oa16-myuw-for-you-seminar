# Features for announcing features

`angularjs-portal` uses portal-wide notifications to notify users about actionable opportunities out in their world. Employees might have a beneft enrollment opportunity, students might have a woefully overdue library book, etc. 

Announcements features are for helping users to be aware of, understand changes to the features and apps in the portal. A new widget might become available, or a new search result type integrated, or so.

## Display options for Announcements

### Interruptive pop-up

MyUW used a maximally interruptive experience to introduce users to the new MyUW on their first use.

### Animated teaser

MyUW uses a less interruptive experience that draws the user's attention with a little motion to announce likely-personally-relevant but not terribly urgent changes.

### Blog-like features page

All the user-relevant feature announcements, previously seen or not, display blog-like at `/features`.

## Tracking seen-ness

`uw-frame` tracks the latest announcement ID a given user has seen, so as to only bother the user with not-yet-seen announcements.

(This last-seen ID is stored into the `KeyValueStore`, an ancillary microservice.)

## Configuration

Like notifications, announcements data is implemented simply as a text file.



## Path forward

Like notifications, while announcements data is currently a text file, it's just a path from the perspective of angularjs-portal and it could instead be generated dynamically.

Current last-seen-ID tracking gets weird for edge cases involving users joining and leaving groups and the announcement item audiences changing. This is likely to be improved when it becomes a pain point.
