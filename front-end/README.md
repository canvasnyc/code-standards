# Front-end Best Practices & Standards

## Table of Contents

1.  [Principles](#principles)
2.  [CSS Standards](#css)
3.  [HTML Standards](#html)
4.  [JS Standards](#js)
5.  [Static Site Generators](#static-sites)

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
* Feature Testing: **Modernizr** https://modernizr.com/

<a name="html"></a>
##HTML Standards
* Preprocessor: **Slim**
* Secondary Preprocessor: **Jade** (node stack)

<a name="js"></a>
##JavaScript Standards
* Preprocessor: **Babel**
* Syntax: **ES6**
* Dom Manipulation Framework: **jQuery**
* Primary UI Framework: **ReactJS**

###When Rails is not Avialable
* Compiler: **Webpack** (if rails is not available)
* Automator: **Gulp** (if rails is not available)

<a name="static-sites"></a>
##Static Site Frameworks
* Middleman
