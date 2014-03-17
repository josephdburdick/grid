##Grid + Stylus Utility Belt


A simple guide to responsive design.<br>
Made by [Adam Kaplan](http://www.adamkaplan.me). Translated into Stylus and extended with [Stylus Utility Belt](https://github.com/josephdburdick/stylus-utilitybelt) by [Joe Burdick](http://joeylabs.com).


####Why bother with responsive?

We want our websites to be useable on all devices by responding to the user’s behavior, screen size and screen orientation.

####A Fragmented World

As of 2013, there are thousands of different devices and screen sizes that browse the internet, so it's impossible to design layouts to target them all. Instead, we must take a more fluid approach to design.

##Steps

####1. Add the Viewport Meta Tag
Place in the `<head>` of your HTML. This enables use of media queries for cross-device layouts.

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

And place this in your CSS for compatibility with IE10+...

```
@-ms-viewport {width: device-width;}
```

####2. Use box-sizing: border-box
Place at the top of your CSS file. The `*` will target all elements on the page.

```
*, *:before, *:after
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;

```

####3. Create a Container
A container holds all elements and controls the page's maximum width. Using a container will make designing for responsive easier! 

####4. Create a Column
A column is a class used for stacking content horizontally. The first margin is removed using the pseudo-class `first-child`.

```
.column
  float: left
  margin-left: 5%

  &:first-child 
    margin-left: 0
```

####5. Create Column Sizes
Add size classes to columns to create a reuseable grid system.


  <div class="container">
    <div class="row">
      <div class="column full"></div>
    </div>
    
    <div class="row">
      <div class="column two-thirds"></div>
      <div class="column one-third"></div>
    </div>
    
    <div class="row">
      <div class="column half"></div>
      <div class="column half"></div>
    </div>
    
    <div class="row">
      <div class="column one-third"></div>
      <div class="column one-third"></div>
      <div class="column one-third"></div>
    </div>
    
    <div class="row">
      <div class="column one-fourth"></div>
      <div class="column one-fourth"></div>
      <div class="column one-fourth"></div>
      <div class="column one-fourth"></div>
    </div>
  </div>


```
.column
  float: left
  margin-left: 5%

  &:first-child
    margin-left: 0

  &.full
    width: 100%

  &.two-thirds
    width: 65%

  &.half
    width: 47.5%

  &.one-third
    width: 30%

  &.one-fourth
    width: 21.25%
```

####6. Create Rows
Columns are wrapped in rows to prevent other elements from stacking next to them, otherwise know as clearing issues. Rows are cleared with a `clearfix`.

```
.row 
  overflow: hidden
  margin-top: 1.5em

  &:first-child 
    margin-top: 0
```


<div class="container">
  <div class="row">
    <div class="column half"></div>
    <div class="column half"></div>
  </div>
  
  <div class="row">
    <div class="column one-third"></div>
    <div class="column one-third"></div>
    <div class="column one-third"></div>
  </div>
</div>


####7. Add a Mobile Breakpoint
If the browser's screen size is within a set range, a media query will replace the CSS the browser uses. This is the bread and butter of responsive web design.

```
@media xs
  html
    font-size: 100%
  section
    padding: 2rem 0
  hr
    margin: 2rem auto

  .column.full,
  .column.two-thirds,
  .column.half,
  .column.one-third,
  .column.one-fourth 
    float: none
    margin: 2em 0 0 0
    width: 100%
```
####8. What's up with that breakpoint in that last example? That isn't normal.</h1>
`xs` is 1 of 11 shorthand breakpoints powered by Stylus Utility Belt. [The following Gist](https://gist.github.com/josephdburdick/9592025.js) is `_breakpoints.styl` in its entirety, showing all available options.  


####9. Breakpoint inspector
Stylus Utility Belt also features a handy-dandy inspector to tell you what breakpoint you're in. It helps with development, is every easy to remove from production, and is totally Javascript-free. Go ahead and try it! If you resize the browser it'll return the current breakpoint. Just remove `@import '_breakpoint_inspector.styl'` from the Stylus sheet. 

####10. Make It Work With IE8
Add the [html5shiv](https://github.com/aFarkas/html5shiv) and [Respond.js](https://github.com/scottjehl/Respond) polyfills in the `<head>` of your HTML to enable html5 elements and responsive breakpoints in Internet Explorer 8.



####Further Reading
* [For a Future-Friendly Web](http://alistapart.com/article/for-a-future-friendly-web)
* [A Book Apart: Responsive Web Design](http://www.abookapart.com/products/responsive-web-design)
* [Don't Forget the Viewport Meta Tag](http://dev.tutsplus.com/articles/quick-tip-dont-forget-the-viewport-meta-tag--webdesign-5972)
* [Understanding the Humble Clearfix](http://fuseinteractive.ca/blog/understanding-humble-clearfix)
* [Beginner’s Guide to Responsive Web Design](http://blog.teamtreehouse.com/beginners-guide-to-responsive-web-design)

####References
* [Android Fragmentation Visualized](http://opensignal.com/reports/fragmentation-2013/)
* [Internet Explorer Box Model](http://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug)
* [Box Model](http://developer.mozilla.org/en-US/docs/Web/CSS/box_model)
* [Force Element To Self-Clear its Children](http://css-tricks.com/snippets/css/clear-fix/)
* [Chrome Developer Tools](http://developers.google.com/chrome-developer-tools/)
* [Animate.css](http://daneden.github.io/animate.css/)
