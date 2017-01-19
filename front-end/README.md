# Front-end Core Standards

## Table of Contents

1.  [Principles](#principles)
2.  [CSS Standards](#css)
3.  [HTML Standards](#html)
4.  [JS Standards](#js)
5.  [Static Site Generators](#static-sites)
6.  [Useful Plugin & Library Reference](#plugins)

<a name="principles"></a>
## Principles

> "Part of being a good steward to a successful project is realizing that
  writing code for yourself is a Bad Idea™. If thousands of people are using
  your code, then write your code for maximum clarity, not your personal
  preference of how to get clever within the spec." - Idan Gazit

* Strive to create loosely coupled, highly reusable code.
* Always keep extensibility in mind.
* Maintain code that is easy read and understand.
* All code in any code-base should look like a single person wrote it, even on a team
  with many contributors.
* When trying to fix an issue, consider removing code before adding to it.
* It is important to strictly enforce the agreed-upon standards.
* Carefully re-evaluate these standards when better systems and conventions are available.
* If it is not possible to defend and support a standard, it should be removed.


<a name="css"></a>
##CSS Standards
* Preprocessor: **SCSS**
* Library: **Compass**
* Resets: **Normalize** https://necolas.github.io/normalize.css/
* Style Guide: [View Guide](https://github.com/canvasnyc/code-standards/blob/master/front-end/css-styleguide.md)

<a name="html"></a>
##HTML Standards
* Preprocessor: **Slim**
* Node Preprocessor: **Jade**
* Style Guide: [View Guide](https://github.com/canvasnyc/code-standards/blob/master/front-end/html-styleguide.md)

<a name="js"></a>
##JavaScript Standards
* Preprocessor: **Babel**
* Syntax: **ES6**
* Dom Manipulation Framework: **jQuery**
* UI Framework: **ReactJS**
* Style Guide: [View Guide](https://github.com/canvasnyc/code-standards/blob/master/front-end/javascript-styleguide.md)


####  * When Rails is *Not* Avialable
* Compiler: **Webpack**
* Automator: **Gulp**

<a name="static-sites"></a>
##Static Site Generators
* **Middleman**

<a name="plugins"></a>
## Useful Plugin & Library Reference
* **Fastclick**: removes 300ms delay on touch devices [source](https://github.com/ftlabs/fastclick)
* **Modernizr**: feature testing [source](https://modernizr.com/)
* **HammerJS**: adds touch gestures [source](http://hammerjs.github.io/)
* **Waypoints**: useful for events triggered by scroll points [source](http://imakewebthings.com/waypoints/)

####  * Common ES6 Polyfills
* `Array.from()`: Needed for IE11 [source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from#Polyfill)
* `Object.assign()`: Needed for IE11 [source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign#Polyfill)
