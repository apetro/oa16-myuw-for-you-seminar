# The app directory

The `angularjs-portal` app directory is simply a view on the uPortal portlet registry.

## Where `angularjs-portal` gets the app directory data from

In a real deployed AngularJS-portal, the registry of applications is read from a uPortal web service.

In `override.js`:

```json
'SERVICE_LOC' : {
  ...
  'marketplace' : {
      'base' : 'marketplace/',
      'entry' : 'entry/',
      'entries' : 'entries.json'
  },
```

In localhost development, that web service is realized by a text file

`/angularjs-portal-mock-portal/src/main/webapp/web/marketplace/entries.json`

## Anatomy of a marketplace entry

See [documentation](http://uw-madison-doit.github.io/angularjs-portal/latest/#/md/app-directory).

`entries.json` is a somewhat awkward JSON view on the `portlet-definition`.

## Future 

The Marketplace entries web service, the relationship of the layout object to the app directory object, it's a little complex and redundant at this point, a good candidate for some tightening.
