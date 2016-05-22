# Solution: add a theme

This solution works the example of adding a theme for Rutgers.

(You can see source code and commits representing the steps for this solution in [a Git branch](https://github.com/apetro/uw-frame/tree/oa16-theming).)

## Research what colors to use

For Rutgers, 

* the [Rutgers Identity System](http://identity.rutgers.edu/) and 
* the colors section of the [Rutgers Visual Identity Manual](http://identity.rutgers.edu/sites/identity/files/RU_IDguide_5.0.pdf)

are elucidating.

## Add the glue LESS file

In `/uw-frame-components/css/themes/` add 'rutgers.less'.

```LESS
@import "../angular.less"; //order is important here
@import "common-variables.less";
@import "rutgers-variables.less";
```

## Add the specific-variables LESS file

In `/uw-frame-components/css/themes/` add the now-referenced 'rutgers-variables.less'.


```LESS
/* MyUW-Madison colors */
@color1: #cc0033;         // Rutgers scarlet
@color2: #990000;         // Medium Red
@color3: #660000;         // Dark Red
@color4: #dfd2b3;         // Cream
@link-color: #00626d;     // Dark Red

@state-info-bg: #E8E4D8;   // Olive Grey
@state-info-text: #000000; // Black

@portlet-titlebar-background-color: #E7D9C1;
@portlet-border-color: #E7D9C1;

@user-portal-logout-btn-text-color: #FFF; //White

@input-border-focus: @color1;
```

## Include the new LESS files in the LESS to CSS compilation

The Java and Node packaging build of `uw-frame` need to be configured to include these LESS files in their respective LESS to CSS compilation steps.

In `/uw-frame-java/pom.xml`:

```xml
<plugin>
  <groupId>org.lesscss</groupId>
  <artifactId>lesscss-maven-plugin</artifactId>
  <version>1.7.0.1.1</version>
  <configuration>
    <!-- ... -->
    <includes>
      <include>uw-madison.less</include>
      <!-- ... -->
      <include>uw-stout.less</include>
      <include>rutgers.less</include> <!-- add this one -->
    </includes>
    <outputFileFormat>{fileName}.${project.version}.css</outputFileFormat>
  </configuration>
  <!-- ... -->
```

In `/uw-frame-static/build.sh`, add 

```
../node_modules/less/bin/lessc -x target/css/themes/rutgers.less > target/css/themes/rutgers.css
```

## Find a logo image

In the case of Rutgers, you could grab one from that visual identity page.

![Example Rutgers shield logo](http://identity.rutgers.edu/sites/identity/files/RU_shield_th.gif)

## Prepare the logo image

Logo images work best when they're exactly 52 pixels tall. I used the MacOS app Acorn to scale the example. There's oodles of tools you can use for this.

## Declare the theme

In `/uw-frame-components/js/frame-config.js`, add a Rutgers entry to the themes array.

```JavaScript
config
  .constant('THEMES', [
    {
      ...
    },
    {
      "name" : "rutgers",
      "crest" : "img/rutgers-52.gif",
      "title" : "MyRutgers",
      "subtitle" : "beta",
      "ariaLabelTitle" : "My Rutgers",
      "crestalt" : "Rutgers crest",
      "group" : "default"
    }
  ])
```
