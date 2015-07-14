# CSS Style Guide


## Table of contents

1.  [Whitespace](#whitespace)
2.  [Formatting](#formatting)
3.  [Naming Conventions](#naming-conventions)
4.  [Comments](#comments)
5.  [Overrides](#overrides)
6.  [Responsive](#responsive)
7.  [SCSS](#scss)
8.  [File Organization](#organization)
9. [Resets](#resets)
10. [Sources](#sources)


<a name="whitespace"></a>
## Whitespace

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
## Formatting

* Always use #hex color codes, unless using rgb/rgba.
* Do not specify units for 0 values. `margin: 0;`
* Try to limit use of shorthand declarations to instances where you must explicitly set 
  all the available values.
* Order properties _alphabetically_.
* Use unit-less line-height. `line-height: 1.5;`
* Other units should tipically be in:
  1. px
  2. ems
  3. %
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

.example--variation {
  @extend .example;
  color: $blue;
}
```


<a name="naming-conventions"></a>
## Naming Conventions

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
## Comments

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
## Overrides

* Avoid using `!important` unless __absolutely necessary__.
* Try to work with the cascade and avoid unecessary overrides.
* Try to avoid chaining selectors `.myselector.another.and-another` but 
  rather create a new specific class.
* Use .ie conditionals to set IE specific code.
* Use Modernizr when necessary to provide feature classes and overrides.


<a name="responsive"></a>
## Responsive

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
// Specify Variables
$break-xs:  320px  !default;
$break-sm:  580px  !default;
$break-md:  768px  !default;
$break-lg:  1024px !default;
$break-xl:  1240px !default;

// Create Mixin
$breakpoints: (
  'xs': ( max-width: $break-sm - 1 ),
  'sm': ( min-width: $break-sm ),
  'md': ( min-width: $break-md ),
  'lg': ( min-width: $break-lg ),
  'xl': ( min-width: $break-xl )
);

@mixin breakpoint($name) {
  @media #{inspect(map-get($breakpoints, $name))} {
    @content;
  }
}

// Embed Mixin
.example-class {
  float: left;
  width: 250px;
  @include respond-to($break-sm) { width: 100%; }
  @include respond-to($break-md) { width: 50%;  }
  @include respond-to($break-lg) { float: none; }
}
```

<a name="scss"></a>
## SCSS
* Use SCSS syntax and never SASS.
* Avoid unnecessary nesting.
* Keep your nesting limited to 3 levels.
* Keep SCSS partials limited to 500 lines.
* Avoid nesting more than 50 consecutive lines.
* Always place `@extend` statements on the first lines of a declaration block.
* Always place regular styles in the middle.
* Always place `@include` statements on the last lines of a declaration block.
* Always place nested selectors after it's parents.
* Use variables for all common numbers, and numbers with meaning.
* Use Compass for all vendor prefixing
* Consolodate all global Variables and Mixins into their own files. 


<a name="organization"></a>
## File Organization

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
## Resets

* Include [normalize](http://necolas.github.io/normalize.css/) , or equivalent, in every project as a foundation.
* When possible specify `box-sizing: border-box` as a global reset.

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
## Sources


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
