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

<a name="layout"></a>
## 3. Layout

* Use HTML5 elements, and generic `<div>`s for layout.
* Do not use tables for anything that isn't tabular data.
* Take advantage of the default behavior of generic `<div>` and `<span>` elements (i.e., don't put `display: inline` on a `div` and don't put `display: block` on a `span`). Likewise, don't redeclare these values.
* Always consider the responsive behavior and flow of elements when structuring markup. Not even CSS can override the order of HTML elements.
  
<a name="accessibility"></a>
## 4. Accessibility

* Use `alt` text on all images.
* Always print out text inside elements that use image replacement.

<a name="sources"></a>
## 5. Sources

* [HTML5 Doctor Element Index](http://html5doctor.com/element-index/)