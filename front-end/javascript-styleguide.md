# JavaScript Style Guide


## Table of contents

1.  [Whitespace](#whitespace)
2.  [Naming Conventions](#naming-conventions)
3.  [Comments](#comments)
4.  [File Organization](#organization)
5.  [Variables](#variables)
6.  [Comparison Operators](#comparison-operators)
7.  [Notes on performance](#performance)
8.  [Sources](#sources)
9.  [Resources](#resources)


<a name="whitespace"></a>
## Whitespace

* Use soft tabs set to 2 spaces.
* Place 1 space before the leading brace.
* Place 1 space before the opening parenthesis in control statements (`if`, `while` etc.). Place no space between the argument list and the function name in function calls and declarations.

  ```javascript
  // bad
  if(isJedi) {
    fight ();
  }

  // good
  if (isJedi) {
    fight();
  }

  // bad
  function fight () {
    console.log ('Swooosh!');
  }

  // good
  function fight() {
    console.log('Swooosh!');
  }
  ```

* Set off operators with spaces.

  ```javascript
  // bad
  const x=y+5;

  // good
  const x = y + 5;
  ```

* Leave a blank line after blocks and before the next statement.
* Do not add spaces inside parentheses or brackets
* Add spaces inside curly braces.


<a name="naming-conventions"></a>
## Naming Conventions

* Avoid single letter names. Be descriptive with your naming.
* Use camelCase when naming objects, functions, and instances.
* Use PascalCase only when naming constructors or classes.
* Do not use trailing or leading underscores.
* Don't save references to `this`. Use arrow functions or [Function#bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind).

  ```javascript
  // bad
  function foo() {
    const self = this;
    return function () {
      console.log(self);
    };
  }

  // bad
  function foo() {
    const that = this;
    return function () {
      console.log(that);
    };
  }

  // good
  function foo() {
    return () => {
      console.log(this);
    };
  }
  ```


<a name="comments"></a>
## Comments

* Use /** ... */ for multi-line comments.
* Use // for single line comments. Place single line comments on a newline above the subject of the comment. Put an empty line before the comment unless it's on the first line of a block.
* Start all comments with a space to make it easier to read.
* Prefixing your comments with FIXME or TODO helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are FIXME: -- need to figure this out or TODO: -- need to implement.


<a name="organization"></a>
## File Organization

* Group controllers, modules, and utility files into their respective directories.
* File names should match what is exported.


<a name="variables"></a>
## Variables

* Always use `const` to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace.
* Use one `const` declaration per variable.
* Group all your `const`s and then group all your `let`s.


<a name="comparison-operators"></a>
## Comparison Operators & Equality

* Use `===` and `!==` over `==` and `!=`
* Conditional statements such as the if statement evaluate their expression using coercion with the `ToBoolean` abstract method and always follow these simple rules:
  - Objects evaluate to true
  - Undefined evaluates to false
  - Null evaluates to false
  - Booleans evaluate to the value of the boolean
  - Numbers evaluate to false if +0, -0, or NaN, otherwise true
  - Strings evaluate to false if an empty string '', otherwise true
* Use shortcuts for booleans, but explicit comparisons for strings and numbers.
* For more information see [Truth Equality and JavaScript](https://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/#more-2108) by Angus Croll.

<a name="performance"></a>
## Notes on performance

* Use chrome DevTools to identify bottlenecks and areas for improvement. [Intro to the Timeline](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/timeline-tool)
* Cache all the selectors needed at the start so as to not repeatedly query the DOM for the same element.
* Remove reference to detached elements (elements that no longer exist in the DOM but are still referenced by a variable). This causes DOM leaks because they cannot be taken care of through garbage collection. [Memory Problems](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots)
* Add and remove event listeners on module initialization and teardown respectively. Additionally, remove an event listener when no longer needed. To ensure an event listener is properly removed, the reference to the callback has to be the exact same as what was added. For example:

  ```javascript
  let button = document.getElementById('button');

  let myClickCallback = () => {
    // `this` needs to be a reference to the outer scope, not the element clicked
    console.log('You clicked ', this);
  }

  // Bad
  button.addEventListener('click', myClickCallback.bind(this));
  button.removeEventListener('click', myClickCallback.bind(this));

  // Good
  let myClickCallbackHandler = myClickCallback.bind(this);

  button.addEventListener('click', myClickCallbackHandler);
  button.removeEventListener('click', myClickCallbackHandler);
  ```

* Avoid DOM read/write loops. Measuring the size of an element forces a relayout in the browser which, if then invalidated by updating styles, requires an additional relayout if more measurements are needed. See [On Layout and Web Performance](https://kellegous.com/j/2013/01/26/layout-performance/).
* When possible, get and store measurements as early as possible so as to avoid unnecessary forced relayouts.
* Declare only needed variables In the spirit of minimizing use of memory, only declare a variable if needed. The 'gotcha' here is having `e` as a parameter in an event callback and then not using it.
* Always use `throttle` and `debounce` for repeated events such as scroll and resize. This limits the rate at which an event callback gets executed. Unless a faster response is needed, our default delay value is 300.


<a name="sources"></a>
## Sources

* [On Layout and Web Performance](https://kellegous.com/j/2013/01/26/layout-performance/)
* [Analyzing Runtime Performance](https://developers.google.com/web/tools/chrome-devtools/rendering-tools/)
* [Debouncing and Throttling Explained](https://css-tricks.com/debouncing-throttling-explained-examples/)

<a name="resources"></a>
## Resources

**Learning ES6**

  - [Draft ECMA 2015 (ES6) Spec](https://people.mozilla.org/~jorendorff/es6-draft.html)
  - [ExploringJS](http://exploringjs.com/)
  - [ES6 Compatibility Table](https://kangax.github.io/compat-table/es6/)
  - [Comprehensive Overview of ES6 Features](http://es6-features.org/)
