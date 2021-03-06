# ki.js

ki.js is a super-tiny jQuery-like JavaScript Library (496 bytes | 320 gzipped)

### Browser support

[ki.js](https://github.com/dciccale/ki.js/blob/master/ki.js) **(recommended)** version is supported by the following browsers: IE9+, Chrome 6+, Safari 5+, Firefox 6+, Opera 11.5+.

[ki.ie8.js](https://github.com/dciccale/ki.js/blob/master/ki.ie8.js) version is supported by the previous browsers including IE8. (623 bytes | 385 gzipped)

## What can I do with ki.js?

With ki.js you can do the basic stuff jQuery can, for example:

### DOM Ready?

```javascript
$(function () {
  // this will be executed when the dom is ready!
  alert('Hey the DOM is ready ;)');
});
```
**This was just ki.js, no jQuery**

### CSS Selectors
Use any CSS selector that exists to get elements from the DOM.

```javascript
$('p:nth-last-of-type(2)');
$('[attribute|=value]');
$('p:not(.note)');
$('p:empty');
```

[See a list of all CSS selectors](http://vogtjosh.com/selectors/)


### Events
Yes, events with the known `.on()` and `.off()` methods

```html
<button>ki.js</button>
```
```javascript
$(function () {
  // ok now that the dom is ready i would like to add some events
  var alertMyName = function () {
    alert('My name is ' + this.textContent); // will allert 'ki.js'
  };

  $('button').on('click', alertMyName);
  // to turn it off just use .off()
  //$('button').off('click', alertMyName);
});
```
You can add any JavaScript event even touch events for mobile, under the hood ki.js uses addEventListener, so feel free to use any valid ECMAScript 5 event.

### .each()
The `each()` is also included in the core of ki.js for easy iterating a DOM collection.

```javascript
$(function () {
  // get all p tags
  $('p').each(function (elem, i) {
    // change color to red
    elem.style.color = 'red';
    // append the index to the text
    elem.textContent += i;
  });
});
```

### Keep the chain!
All methods of ki.js are chainable, just like jQuery.

## Plugins?
Yeah, you could write plugins for ki.js if you want, fork the project for making them, keep them super super xxs and I promise to merge them into the official repo.

### How to make plugins?
Just add your methods to the prototype of ki.js and you're done.
For example, let's add a `text()` method for setting or getting the text of the elements, in the tiniest way I can think of:

```javascript
// minified is 106 bytes
$.prototype.text = function (a) {
  return a === a + '' ? this.each(function (b) {
    b.textContent = a
  }) : this[0].textContent
};
```

Now use the plugin just like the other methods:
```javascript
$(function () {
  // <p>hello</p>

  // get the text from the p tag
  console.log($('p').text()); // hello

  // set another text
  $('p').text('bye'); // bye
});
```
<hr>
<strong>Create your own plugin and let's make the tiniest JavaScript Library ever!
Remember to write byte-saving code, see this [useful resource for JavaScript byte-saving techniques](https://github.com/jed/140bytes/wiki/Byte-saving-techniques) written by 140byt.es community</strong>
<hr>

## Where can i use ki.js?

In every cool and modern browser.

## The Code
The code of ki.js was written for byte-saving, so I don't recommend using this script for a real application or website.
It was done for fun, and the funniest part is that it actually works :)

## Building

To build, you need [Grunt](http://gruntjs.com/). If you haven't used grunt before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started).

Here are some of the tasks that grunt can run:

* grunt normal -- compile ki.js to ki.min.js
* grunt ie -- compile ki.ie8.js to ki.ie8.min.js

Running `grunt` (default task) is just mapped to the `uglify:normal` task.

## License
See [LICENSE.txt](https://raw.github.com/dciccale/ki.js/master/LICENSE.txt)
