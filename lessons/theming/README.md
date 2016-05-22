# How theming works in uw-frame

See also theming documentation.

## Trying it out

`uw-frame` includes a settings page at `/settings` that allows selecting among the available themes.

![Theme selector](http://goo.gl/l9KKtM)

## Anatomy of a theme

### LESS files

`uw-frame-components` includes most of the substance of uw-frame, abstracting this so that it can be used in both the .war and the Node package `uw-frame` packagings.

In `uw-frame-components/css/themes/` there are a couple of files for each theme.

There's an `{institution_name}.less` file that formulaically combines the generic LESS shared across all themes with the institution-specific LESS that makes this theme special.

```LESS
@import "../angular.less"; //order is important here
@import "common-variables.less";
@import "uw-madison-variables.less";
```

and then there's an `{institution_name}-variables.less` that sets the colors that are particular to that theme.

```LESS
/* MyUW-Madison colors */
@color1: #b70101;         // Badger Red
@color2: #990000;         // Medium Red
@color3: #660000;         // Dark Red
@color4: #F7F5E8;         // Cream
@link-color: #660000;     // Dark Red

@state-info-bg: #E8E4D8;   // Olive Grey
@state-info-text: #000000; // Black

@portlet-titlebar-background-color: #E7D9C1;
@portlet-border-color: #E7D9C1;

@user-portal-logout-btn-text-color: #FFF; //White

@input-border-focus: @color1;
```

### Images

Themes include a logo. This logo should be 52 pixels tall.

Logos go in `/uw-frame-components/img/`.

### Theme metadata

Themes are declared in `/uw-frame-components/js/frame-config.js` in the `THEMES` constant array.

```JavaScript
...
config
  .constant('THEMES', [
    {
      "name" : "uw-madison",
      "crest" : "img/uw-madison-52.png",
      "title" : "MyUW",
      "subtitle" : null,
      "ariaLabelTitle" : "My U W",
      "crestalt" : "UW Crest",
      "group" : "UW-Madison",
      "mascotImg" : "img/bucky.gif"
    },
    {
      "name" : "uw-river-falls",
      "crest" : "img/uw-riverfalls-52.png",
      "title" : "MyUW",
      "subtitle" : "beta",
      "ariaLabelTitle" : "My U W",
      "crestalt" : "UW River Falls Logo",
      "group" : "UW System-River Falls"
    },
      ...
```

Themes also need to be declared in build configuration so that they are included in the step that compiles LESS to CSS.

That is, in `/uw-frame-java/pom.xml` configuration of the `lesscss-maven-plugin` and in `/uw-frame-static/build.sh`.

## How default theme selection works

You can switch your theme selection by settings a value in browser LocalStorage, via the handy `/settings` UI.

But how does `uw-frame` decide what theme to show you by default?

`/uw-frame-components/app-config.js` sets an `APP_FLAGS` --> `defaultTheme`. This can either be the zero-based index of which theme you'd like to be default in the array of themes, or can  be the special value "group" which will cause uw-frame to default each user to the first theme in the array with a `group` value that matches the name of a (uPortal) group of which the user is a member.

Note that in your overlays on uw-frame you need not overwrite `app-config.js` wholesale; you can instead tweak it via `override.js` .


# Related: uPortal theming

To the extent that your portal involves rendering JSR-286 (or JSR-168) portlets via uPortal's rendering pipeline, in say maximized window state or so, you may need to replicate your frame theme as a uPortal Respondr theme or so.

# Future changes

In the future, uw-frame theming may be richer, with more of the colors having more of an effect and with additional settings to adjust.

In the future, uw-frame may adopt Material Design, perhaps after upgrading to AngularJS 2 and using the in-development Angular Material add-on for AngularJS 2.

Material Design comes with its own theming and color pallet conceptual framework as well as concrete technology for this. uw-frame theming would need to be reconciled with Material Design theming at that juncture.
