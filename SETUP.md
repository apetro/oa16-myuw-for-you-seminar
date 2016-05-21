Stuff to download, stuff to set up, how to tell that it's ready.

# Stuff you need

 * Maven
 * angularjs-portal
 * node
 * npm
 * uw-frame

## Maven

You'll need Maven to build and run `angularjs-portal`.

https://maven.apache.org/

You're in good shape when

```
mvn -v
```

prints something reasonable, like

```
Apache Maven 3.1.1 (0728685237757ffbf44136acec0402957f723d9a; 2013-09-17 11:22:22-0400)
Maven home: /usr/local/Cellar/maven/3.1.1/libexec
Java version: 1.7.0_71, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk1.7.0_71.jdk/Contents/Home/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.11.4", arch: "x86_64", family: "mac"
```

## angularjs-portal

angularjs-portal implements some of the user experiences in the new MyUW, so you'll need a copy of it that you can build and run.

This tutorial uses `angularjs-portal` version `4.2.1.6`.

### Download angularjs-portal 

* The [4.2.1.6 release page](https://github.com/UW-Madison-DoIT/angularjs-portal/releases/tag/angularjs-portal-parent-4.2.1.6)
* links at bottom of release page to download .zip or .tar.gz)

Put the zip file somewhere you can find. `~/code` for instance.

### Un-zip it 

(Double-clicking the zip file works to un-zip it in some environments).

### Re-name the un-zipped folder

By default it's got the name of the tag, which is precise but awkward.

Renaming it to `ng-portal` would be fine.

So you'll end up with

`~/code/ng-portal/`

and a bunch of files and folders within `ng-portal`.

### Get there in a terminal

For example,

```
cd 
cd code
cd ng-portal
```

### Run it!

Supposing you don't already have a server running on port `8080`, 

```
mvn clean package && mvn jetty:run
```

If you do already have a server running on port `8080` (e.g. tomcat), stop that first.

### Take a look in a web browser

http://localhost:8080/

If something like this renders, you're in good shape.

![Screenshot of AngularJS-portal rendering against fake data](http://goo.gl/QcdXkO)

That's an ad-hoc jetty server that's serving that up. Pretty neat.

You can stop it again by `control-C` in the terminal that's running it, that is the one in which you ran `... mvn jetty:run`.

## node

You'll need `node` to build `uw-frame`.

https://nodejs.org/en/

Node is successfully installed when you can run `node -v` and get back a reasonable version number.

```
$ node -v
v5.8.0
```

## npm

You'll need `npm` to build `uw-frame`.

https://docs.npmjs.com/getting-started/installing-node

npm is successfully installed when you can run `npm -v` and get back a reasonable version number.

``` 
npm -v
3.7.3
```

## uw-frame

This tutorial works with uw-frame 2.3.0.

### Download uw-frame

https://github.com/UW-Madison-DoIT/uw-frame/releases/tag/v2.3.0

Put it somewhere reasonable.

`~/code/` is a good spot

### Un-zip it

### Run it

```
npm run static
```

It's a good sign if that runs for a while and then concludes with

```
Superstatic started.
Visit http://localhost:3474 to view your app.
```

### Take a look in a web browser

http://localhost:3474/

You're in good shape if you see something like

![uw-frame rendering](http://goo.gl/eDBxk6).
