# Exercise: editing the mock app directory

Take a look at the localhost mock `entries.json` and try your hand at tweaking it a bit.

This gets tedious quickly, a good reason to integrate with uPortal and manage this data in the database instead. :smile:

Hints:

* It's `mvn clean package && mvn jetty:run` to run `angularjs-portal` from the root of that project.
* Quotes within quotes in JSON need to be escaped effectively.

`angularjs-portal` caches the app directory client-side for performance, since it doesn't change often.

But it'll change when you change it!

You can easily clear your browser cache of `angularjs-portal` content at

http://localhost:8080/web/settings

via the controls in the "Danger Zone", which are not at all dangerous. `angularjs-portal` gracefully re-loads whatever it can't find in local storage.

![Tool for clearing cache](http://goo.gl/pdDItb)
