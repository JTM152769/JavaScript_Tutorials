## 1.Introduction

Now that we already know how to program a little, it's time to dive into the specifics of the browser and front-end development.

What is frontend development in general?

Modern sites have a high degree of interactivity. Pages are reloading less and less, and content manipulations take place right on the spot. Software solutions have become so complex (complex) that even now full-featured development environments (for example, hexlet ide), programs like Photoshop or packages similar to Microsoft Office are being implemented in the browser.

But what can we say, there is a large industry of games created for browsers. Moreover, thanks to hardware support, these games are not inferior to what is being done for a regular desktop.

The language, which was originally used as a way to add snowflakes to the site, has become a powerful tool in the hands of professionals.

Currently, javascript is the only language executed by browsers.

By the way, a large number of languages ​​are either created on top of js or allow you to 
translate your code into js. These languages ​​include: clojurescript, 
typescript, kotlin, java, elm.

But one language is not enough to revive the page. The main value is that browsers add features to js that allow you to manipulate the contents of the page, as well as control the browser itself. Most of these features are standardized and described in the HTML5 specifications. Here are some of them:

```
Content Manipulation
Appearance Management
Reaction to user actions
Work with cookies
Browser control
Interaction with the server
Playing video
Browser Database
Multitasking Web Workers
Io
2D / 3D drawing
```
From the point of view of the language, most of these possibilities look like certain global objects with which you can interact in the program. The most basic and key object of this system is the representation of the DOM tree. Since the DOM is a global object, when working with it, our favorite higher-order functions such as map are almost never used. The fact is that a change in DOM always happens directly, which means that the processing of collections does not generate new collections. Almost all mass operations are done using the forEach function.

In this course, we will learn to introduce js to the site, go through the main ways of manipulating the page, learn about polyfills, make our first ajax request and discover the world of events.

After this course you will be able to try your hand at creating simple front-end games (in practice after the courses).

## 2. JavaScript in browser

The main way to add js code to a page is to use a tag script.

## 2.1 Inline scripts

Similar tags can be any number in any places inside bodyor head. True, the location depends on the possibilities, but we will consider this question later.

```javascript
<html>
  <body>
    <script>
      const greeting = 'hello, world!';
      alert(greeting);
    </script>
  </body>
</html>
```
The easiest way to start interacting with the browser is to call a function alert. Although in real code it is almost never used, but the creators of courses in which programming training is conducted through a browser are very fond of it. Click

to see the result of this function.

In addition alert to user interaction, you can use functions and
All these functions are present only in browsers and are not available in server versions js. This is the first example when we see how the browser “expands” js, adding new features to it. But not the possibilities of the language itself, the language remains the same, but the possibilities of interaction with the environment.

## 2.2 External scripts

Inline scripting is usually used for small pieces of code, or to call code loaded from external scripts. External scripts are loaded as follows:

```javascript
<body>
<html>
  <head>
    <script src="/assets/application.js"></script>
  </head>
  <body>
  </body>
</html>
```
Quite often you can see a similar download option:

```javascript
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/core.js"></script>
```
In the example above, the file is loaded from a [CDN](https://ru.wikipedia.org/wiki/Content_Delivery_Network). , which may have certain advantages in download speed.

## 2.3 Speed
Depending on where in the document the tags appear script, you can observe serious changes in both the speed of the site rendering and the download speed.

## 2.4 Server (Nodejs) vs Client (Browser)
The browser is missing a lot of those things that we used to deal with when working in a server environment. Among them:

## 2.5 Standard library
About library 4  you can forget. No out of the box assert, events, net, http, urland all the rest. For any simple task you will have to connect the library from npm.

## 2.6 Modules
Until recently, a modular system in browsers did not exist. Now it appears, but so far only in the experimental version.

At the moment, any downloaded code works in the global scope. This behavior led to a large number of bypass maneuvers used everywhere for manual isolation of js pieces from each other.

``` javascript
<html>
  <body>
    <script>
      const greeting = 'hello, world!';
    </script>
    <script>
      alert(greeting);
    </script>
  </body>
</html>
```
The most common method of isolation is called Immediately-Invoked Function Expression. Its principle of operation is extremely simple: all the code that must be executed in the browser is wrapped in an anonymous function, which is immediately called:

```javascript
(function() {
 // some code…
})();
```
As you will see later, modern assembly systems save us from having to do such manipulations with our hands. We can continue to use the usual and full javascript.

## 2.7 Versions and engines
Another major flaw jsin the browser is that the implementation jsin different browsers is different and sometimes quite significant. Moreover, even different versions of the same browser may differ catastrophically. Moreover, this problem cannot be solved; it is a consequence of the very nature of the frontend. Each user will have the browser that they like, the version to which he did not forget to upgrade.

## 2.8 Assembly
Fortunately, the modern world of the frontend was able to get out of this situation. We can still use all (almost) modern features js, including a system of modules. Perhaps this is due babelon the one hand and similar collectors webpackon the other. Well, it is impossible not to mention the polyfill, which will be devoted to a separate lesson.

The principle of operation of this bundle is that the collector collects all our resources (css, fonts, images) and files with code according to certain rules, passes them through handlers, for example, babel, and we get files ready for use in the browser.

![Screenshot](screenshot.png)









