# HTML Style Guide

## Table of contents

1.  [General Principles](#principles)
2.  [HTML5] (#html5)
3.  [Layout](#layout)
4.  [Accessibility](#accessibility)
5.  [Seo](#seo)
6.  [Attributes](#attributes)
7.  [Meta Tags](#meta)
8.  [Templating Language](#templating)
00. [Sources](#sources)

<a name="principles"></a>
## 1. General Principles

* HTML is content-driven markup language. The elements being used should reflect the content, its intention and its behavior as much as possible.
* Use soft-tabs with a two space indent. Spaces are the only way to guarantee code renders the same in any person’s environment.
* Organize all css in the `<head>` and javascript at the bottom of the `body` tag.
* Paragraphs of text should always be placed in a `<p>` tag. Never use multiple `<br>` tags.
* Items in list form should always be in `<ul>`, `<ol>`, or `<dl>`. Never use a set of `<div>` or `<p>`.
* Do not use closing slashs on self closing elements: `<br>`, `<hr>`, `<img>`

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
## 4. Accessibility

* Only use image replacement when absolutely necessary.
* Always include labels on form elements (even if they need to be hidden).
* Wrap radios, checkboxes and their text in labels.
* Include a `tabindex` attribute on all form elements.
* When possible adjust for visually impaired users: [testing tool](https://chrome.google.com/webstore/search/NoCoffee%20Vision%20Simulator?hl=en&gl=US).
* Only add a new tag when absolutely necessary or required by semantics to avoid over-nesting.
* Make important hidden text available to screen readers.

<a name="seo"></a>
## 5. SEO

* Use `alt` attributes on all images.
* Never use images in place of important text.
* Always print out hidden text inside elements that use image replacement.
* Use `title` attributes on all links.
* Be sure to include a live text `h1` tag on every page with relavant contextual copy.
* Do not wrap important content inside JS (exceptions based on framework).
* Always include a relavant `title` meta tag.
* When formatting title meta tags always include the site name after the page description, not before. `<meta name="title" content="Contact Us | Canvas">`
* Always include a relavant `desc` meta tag.
* When necessary use [schema](http://schema.org/) to enhance SEO.

<a name="attributes"></a>
## 6. Attributes

* Add attributes in a consistent order to improve readability.
```
<a href="link-1" id="id-1" class="class-1" title="title-1">Link 1</a>
<a href="link-2" id="id-2" class="class-2" title="title-2">Link 2</a>

a#id-1.class-1 href="link-1" title="title-1"
a#id-2.class-2 href="link-2" title="title-2"
```

<a name="meta"></a>
## 7. Meta Tags

* In general, include all of the following meta tags including all favicon formats.
```
head
  meta charset="utf-8"
  meta content="IE=edge,chrome=1" http-equiv="X-UA-Compatible"
  title = "Page Title"
  meta name="description" content="Pge Description"
  meta name="copyright" content="(c) 2015 example site"
  meta name="viewport" content="user-scalable=0, width=device-width, initial-scale=1.0,  minimum-scale=1.0, maximum-scale=1.0"
  meta name="apple-mobile-web-app-capable" content="yes"
  meta name="apple-mobile-web-app-status-bar-style" content="black"
  = favicon_tag "/apple-touch-icon-57x57.png", rel: "apple-touch-icon", sizes: "57x57"
  = favicon_tag "/apple-touch-icon-60x60.png", rel: "apple-touch-icon", sizes: "60x60"
  = favicon_tag "/apple-touch-icon-72x72.png", rel: "apple-touch-icon", sizes: "72x72"
  = favicon_tag "/apple-touch-icon-76x76.png", rel: "apple-touch-icon", sizes: "76x76"
  = favicon_tag "/apple-touch-icon-114x114.png", rel: "apple-touch-icon", sizes: "114x114"
  = favicon_tag "/apple-touch-icon-120x120.png", rel: "apple-touch-icon", sizes: "120x120"
  = favicon_tag "/apple-touch-icon-144x144.png", rel: "apple-touch-icon", sizes: "144x144"
  = favicon_tag "/apple-touch-icon-152x152.png", rel: "apple-touch-icon", sizes: "152x152"
  = favicon_tag "/apple-touch-icon-180x180.png", rel: "apple-touch-icon", sizes: "180x180"
  = favicon_tag "/favicon-32x32.png", rel: "icon", sizes: "32x32"
  = favicon_tag "/favicon-194x194.png", rel: "icon", sizes: "194x194"
  = favicon_tag "/favicon-96x96.png", rel: "icon", sizes: "96x96"
  = favicon_tag "/android-chrome-192x192.png", rel: "icon", sizes: "192x192"
  = favicon_tag "/favicon-16x16.png", rel: "icon", sizes: "16x16"
  link rel="manifest" href="/manifest.json"
  meta name="msapplication-TileColor" content="#ffffff"
  meta name="msapplication-TileImage" content="/mstile-144x144.png"
  meta name="theme-color" content="#ffffff"
  = stylesheet_link_tag "examplecss"
```

<a name="templating"></a>
## 8. Technology

* Always use [Slim](http://slim-lang.com/) in ruby/rails environments including [Middleman](https://middlemanapp.com/).
* Always use [Middleman](https://middlemanapp.com/) for static sites/sites with no back end.
* Use [Jade](http://naltatis.github.io/jade-syntax-docs/) in all node based environments.
* Do not mix preprocessing languages and remain consistent.

<a name="sources"></a>
## 00. Sources

* [HTML5 Doctor Element Index](http://html5doctor.com/element-index/)
* [Favicon Format Generator](http://realfavicongenerator.net/)
