# HTML Style Guide

## Table of contents

1.  [Principles](#principles)
2.  [HTML5] (#html5)
3.  [Layout](#layout)
4.  [Accessibility](#accessibility)
5.  [Sources](#sources)

<a name="principles"></a>
## 1. Principles

* HTML is content-driven markup language. The elements being used should reflect the content, its intention and its behavior as much as possible.
* Strive to write clear code such that someone with little or no understanding of programming could view it and have a reasonable idea of what the content is.


<a name="html5"></a>
## 2. HTML 5

* Always use the HTML5 doctype: `<!doctype html>`
* Use HTML5 semantic elements when appropriate. If in doubt, refer to [HTML5 Doctor](http://html5doctor.com/element-index/) for a description of elements.
* Use section and article tags based on correct semantics and never interchangeably.

<a name="layout"></a>
## 3. Layout

* Use HTML5 elements, and generic `<div>`s for layout.
* Do not use tables for anything that isn't tabular data.
* Take advantage of the default behavior of generic `<div>` and `<span>` elements (i.e., don't put `display: inline` on a `div` and don't put `display: block` on a `span`). Likewise, don't redeclare these values.
* Always consider the responsive behavior and flow of elements when structuring markup. Not even CSS can override the order of HTML elements.
  
<a name="accessibility"></a>
## 4. Accessibility & SEO

* Use `alt` attributes on all images.
* Never use images in place of important text.
* Always print out hidden text inside elements that use image replacement.
* Only use image replacement when absolutely necessary.
* Use `title` attributes on all links.
* Always include labels on form elements (even if they need to be hidden).
* Include a `tabindex` attribute on all form elements.
* When possible adjust for visually impaired users: [testing tool](https://chrome.google.com/webstore/search/NoCoffee%20Vision%20Simulator?hl=en&gl=US).
* Be sure to include a live text `h1` tag on every page with relavant contextual copy.
* Only add a new tag when absolutely necessary or required by semantics to avoid over-nesting.
* Make important hidden text available to screen readers.
```
%visuallyhidden {
  margin: -1px;
  padding: 0;
  width: 1px;
  height: 1px;
  overflow: hidden;
  clip: rect(0 0 0 0);
  clip: rect(0, 0, 0, 0);
  position: absolute;
}
```

<a name="sources"></a>
## 5. Sources

* [HTML5 Doctor Element Index](http://html5doctor.com/element-index/)
