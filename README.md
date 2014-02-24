# [Headroom.js](http://wicky.nillia.ms/headroom.js)

**Give your pages some headroom. Hide your header until you need it.**

## What's it all about?

Headroom.js is a lightweight, high-performance JS widget (with no dependencies!) that allows you to react to the user's scroll. The header on [this site](http://wicky.nillia.ms/headroom.js) is a living example, it slides out of view when scrolling down and slides back in when scrolling up.

### Why use it?

Fixed headers are a popular approach for keeping the primary navigation in close proximity to the user. This can reduce the effort required for a user to quickly navigate a site, but they are not without problems…

Large screens are usually landscape-oriented, meaning less vertical than horizontal space. A fixed header can therefore occupy a significant portion of the content area. Small screens are typically used in a portrait orientation. Whilst this results in more vertical space, because of the overall height of the screen a meaningfully-sized header can still be quite imposing.

Headroom.js allows you to bring elements into view when appropriate, and give focus to your content the rest of the time.

### How does it work?

At it's most basic headroom.js simply adds and removes CSS classes from an element in response to a scroll event:

```html
<!-- initially -->
<header class="headroom">

<!-- scrolling down -->
<header class="headroom headroom--unpinned">

<!-- scrolling up -->
<header class="headroom headroom--pinned">
```

Relying on CSS classes affords headroom.js incredible flexibility. The choice of what to do when scrolling up or down is now entirely yours - anything you can do with CSS you can do in response to the user's scroll.

## Usage

Using headroom.js is really simple. It has a pure JS API, plus an optional jQuery/Zepto plugin and AngularJS directive.

### With pure JS

Include the `headroom.js` script in your page, and then:

```js
// grab an element
var myElement = document.querySelector("header");
// construct an instance of Headroom, passing the element
var headroom  = new Headroom(myElement);
// initialise
headroom.init();
```

### With jQuery/Zepto

Include the `headroom.js` and `jQuery.headroom.js` scripts in your page, and then:

```js
// simple as this!
// NOTE: init() is implicitly called with the plugin
$("header").headroom();
```

The plugin also offers a data-* API if you prefer a declarative approach.

```html
<!-- selects $("[data-headroom]") -->
<header data-headroom>
```

Note: Zepto's additional [data module](https://github.com/madrobby/zepto#zepto-modules) is required for compatibility.

### With AngularJS

Include the `headroom.js` and `angular.headroom.js` scripts in your page, and then:

```html
<header headroom></header>
<!-- or -->
<headroom></headroom>
<!-- or with options -->
<headroom tolerance='0' offset='0' classes="{pinned:'headroom--pinned',unpinned:'headroom--unpinned',initial:'headroom'}"></headroom>
```

## Options

Headroom.js can also accept an options object to alter the way it behaves. You can see the default options by inspecting `Headroom.options`. The structure of an options object is as follows:

```js
{
    // vertical offset in px before element is first unpinned
    offset : 0,
    // scroll tolerance in px before state changes
    tolerance : 0,
    // css classes to apply
    classes : {
        // when element is initialised
        initial : "headroom",
        // when scrolling up
        pinned : "headroom--pinned",
        // when scrolling down
        unpinned : "headroom--unpinned"
        // when scroll position is at the very top
        top : "headroom--top"
    },
    // callback when pinned, `this` is headroom object
    onPin : function() {},
    // callback when unpinned, `this` is headroom object
    onUnpin : function() {},
    // callback when scroll position is at the very top, `this` is headroom object
    onTop : function() {},
    // callback when we've scrolled away from the top, `this` is headroom object
    onUntop : function() {}
}
```

## Examples

Head over to the [headroom.js playroom](http://wicky.nillia.ms/headroom.js/playroom/) if you want see some example usages. There you can tweak all of headroom's options and apply different CSS effects in an interactive demo.

## Browser support

Headroom.js is dependent on the following browser APIs:

* [requestAnimationFrame](http://caniuse.com/#feat=requestanimationframe)
* [classList](http://caniuse.com/#feat=classlist)
* [Function.prototype.bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind#Browser_compatibility)

All of these APIs are capable of being polyfilled, so headroom.js can work with less-capable browsers if desired. Check the linked resources above to determine if you must polyfill to achieve your desired level of browser support.

## Contributions & Issues

Contributions are welcome. Please clearly explain the purpose of the PR and follow the current style.

Issues can be resolved quickest if they are descriptive and include both a reduced test case and a set of steps to reproduce.

## License

Licensed under the [MIT License](http://www.opensource.org/licenses/mit-license.php).
