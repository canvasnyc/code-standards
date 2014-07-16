# CSS Style Guide


## Table of contents

1.  [Principles](#principles)
2.  [Whitespace](#whitespace)
3.  [Formatting](#formatting)
4.  [Naming Conventions](#naming-conventions)
5.  [Comments](#comments)
6.  [Overrides](#overrides)
7.  [Responsive](#responsive)
8.  [SCSS](#scss)
9.  [File Organization](#organization)
10. [Resets](#resets)
11. [Sources](#sources)


<a name="principles"></a>
## 1. Principles


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


<a name="whitespace"></a>
## 2. Whitespace

* Configure your IDE to use soft-tabs with a two space indent. Spaces guarantee code 
  will renders the same all environment.
* Trim trailing white spaces.
* Add a space after the `:` in property declarations.
* Separate each ruleset by a blank line.
* One selector per line, one rule per line
* Place closing braces of selectors on their own line.
* Include a space after each comma in comma-separated property or function values.
* Large blocks of single declarations can use a single-line format. In this case, a 
  space should be included after the opening brace and before the closing brace.

<a name="formatting"></a>
## 3. Formatting

* Always use #hex color codes, unless using rgb/rgba.
* Do not specify units for 0 values. `margin: 0;`
* Try to limit use of shorthand declarations to instances where you must explicitly set 
  all the available values.
* Order properties:
  1. _by related values_
  2. _alphabetically_
* Use unit-less line-height. `line-height: 1.5;`
* Other units should tipically be in:
  1. _px_
  2. _ems_
  3. _%_
* Use double rather than single quotation marks. `input[type="text"]` not `input[type='text']`

#### Example:

```
// Example spacing, using BEM syntax
.example {
  @extend .an-extention;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 14px;
  line-height: 1.5;
  margin: 0;
  padding-bottom: 0;
  @include mixin(example-mixin);
  
  .example__component {
    background: #AAA;
    display: block;

    &:hover {
      background: #CCC;
    }
  }
}
```


<a name="naming-conventions"></a>
## 4. Naming Conventions

* Use [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) naming conventions.
* Provide clear names for your selectors.
* Do not unnecessarily abriviate selectors, and reduce readability.
* Strive to create loosely coupled, modular code that can be easily reused regardless of 
  its container or contents.
* Avoid the use of ID’s. The negligible performance difference is not worth the limitations.
* When a class is applied or used as a selector for JavaScript, prefix the class with js-.
* Never reference js- prefixed class from a CSS file. js- should be used exclusively in JS files.
* Use the is- prefix for state rules that are shared between CSS and JS.
* Make JS selector’s names clearly represent their function. `.js-toggle-menu` , `.is-active`.


<a name="comments"></a>
## 5. Comments

* Well commented code is extremely important. Take time provide information about your 
  code, it’s limitations, and any non-obvious information.
* When possible, use KSS formatting to determine comment formatting and provide a style guide.
* Always add an introductory comment to all partials to provide clarity about the files 
  contents and purpose.
* Use hierarchical comments to divide and organize your files.
* Try to make comments concise and intuitive.
* It’s a good idea to configure your editor to provide you with shortcuts to output 
  agreed-upon comment patterns.

#### Example:

```
//  ==========================================================================
//
//  Section comment block: for specs or table of contents
//
//  Project: Exmaple Project
//  Version: 1.1
//  Last change: 05/06/2014
//  Primary use: Examples
//
//  ==========================================================================


//  ==========================================================================
//  Section Introductory comment block: Standard
//  ==========================================================================


//  Sub-section comment block
//  __________________________________________________________________________


//  ------------------------------------------
//
//  Comment on multiple lines
//  
//  This is an Example of a long comment that
//  spans multiple line.
//  
//  Use this format for long descriptions and 
//  more detailed documentation 
//
//  ------------------------------------------


//  Basic comment
```

<a name="overrides"></a>
## 6. Overrides

* Avoid using `!important` unless __absolutely necessary__.
* Try to work with the cascade and avoid unecessary overrides.
* Try to avoid chaining selectors `.myselector.another.and-another` but 
  rather create a new specific class.
* Use .ie conditionals to set IE specific code.
* Use Modernizr to provide feature classes and overrides.


<a name="responsive"></a>
## 7. Responsive

* Always build mobile first. This will greatly reduce the weight on mobile and 
  significantly reduces necessary overrides through media queries.
* Always specify your media query breakpoints via variables.
* Nest media queries inside the original selector, allow them to be easily located
  and modified. If Sprockets is available combine all media queries for production 
  with: [Sprockets Media Query Combiner.](https://github.com/aaronjensen/sprockets-media_query_combiner.)
* When nesting creates readability issues, include your media quierys at the bottom
  of that partial.

#### Example:

```
// Set Variables
$break-small: 24em;
$break-large: 46.8em;

// Create Mixin
@mixin respond-to($media) {
  @if $media == handhelds {
    @media only screen and (max-width: $break-small) { @content; }
  }
  @else if $media == medium-screens {
    @media only screen and (min-width: $break-small + 1) and (max-width: $break-large - 1) { @content; }
  }
  @else if $media == wide-screens {
    @media only screen and (min-width: $break-large) { @content; }
  }
}

// Embed Query
.example-class {
  float: left;
  width: 250px;
  @include respond-to(handhelds)      { width: 100% ;}
  @include respond-to(medium-screens) { width: 50%; }
  @include respond-to(wide-screens)   { float: none; }
}
```

<a name="scss"></a>
## 8. SCSS
* Use SCSS syntax and never SASS.
* Avoid unnecessary nesting.
* Keep your nesting limited to 3 levels.
* Keep SCSS partials limited to 500 lines.
* Avoid nesting more than 50 lines.
* Always place `@extend` statements on the first lines of a declaration block.
* Always place regular styles in the middle.
* Always place `@include` statements on the last lines of a declaration block.
* Always place nested selectors after it's parents.
* Use variables for all common numbers, and numbers with meaning.
* Use Compass for all vendor prefixing
* Consolodate all global Variables and Mixins into their own files. 


<a name="organization"></a>
## 9. File Organization

#### Folder Structure:

```
sass/ 
| 
|– base/ 
|   |– _reset.scss       # Reset/normalize 
|   |– _typography.scss  # Typography rules 
|   ...                  # Etc… 
| 
|– components/ 
|   |– _buttons.scss     # Buttons 
|   |– _carousel.scss    # Carousel 
|   |– _cover.scss       # Cover 
|   |– _dropdown.scss    # Dropdown 
|   |– _navigation.scss  # Navigation 
|   ...                  # Etc… 
| 
|– helpers/ 
|   |– _variables.scss   # Sass Variables 
|   |– _functions.scss   # Sass Functions 
|   |– _mixins.scss      # Sass Mixins 
|   |– _helpers.scss     # Class & placeholders helpers 
|   ...                  # Etc… 
| 
|– layout/ 
|   |– _grid.scss        # Grid system 
|   |– _header.scss      # Header 
|   |– _footer.scss      # Footer 
|   |– _sidebar.scss     # Sidebar 
|   |– _forms.scss       # Forms 
|   ...                  # Etc… 
| 
|– pages/ 
|   |– _home.scss        # Home specific styles 
|   |– _contact.scss     # Contact specific styles 
|   ...                  # Etc… 
| 
|– themes/ 
|   |– _theme.scss       # Default theme 
|   |– _admin.scss       # Admin theme 
|   ...                  # Etc… 
| 
|– vendors/ 
|   |– _bootstrap.scss   # Bootstrap 
|   |– _jquery-ui.scss   # jQuery UI 
|   ...                  # Etc… 
| 
| 
`– style.scss             # primary Sass file
```
[Reference](http://www.sitepoint.com/architecture-sass-project/)


<a name="resets"></a>
## 10. Resets

* Include [normalize](http://necolas.github.io/normalize.css/) in every project as a foundation.
* When possible `box-sizing: border-box` as a global reset.

#### Example:

```
// SCSS and Compass

html {
  @include box-sizing(border-box);
}

*, 
*:before, 
*:after {
  @include box-sizing(inherit);
}
```


<a name="sources"></a>
## 11. Sources


#### Style Guide Examples

* [GitHub](https://github.com/styleguide/css)
* [Idiomatic](https://github.com/necolas/idiomatic-css)
* [Google](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
* [ThinkUp](https://github.com/ginatrapani/ThinkUp/wiki/Code-Style-Guide:-CSS)
* [CSS Wizardry](http://csswizardry.com/2012/04/my-html-css-coding-style/)
* [Wordpress](http://make.wordpress.org/core/handbook/coding-standards/css/)

#### Style Patterns

* [BEM](http://bem.info/) / [BEM Guide](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
* [SMACSS](http://smacss.com/)
* [Atomic CSS](http://bradfrostweb.com/blog/post/atomic-web-design/)
* [OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)
