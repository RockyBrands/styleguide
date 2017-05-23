---
layout: page
title: ADA Compliance Requirements
description: Required action items for our third party developers
---
# PFS web

The following are required changes to the current template in order to comply with ADA AA requirements.

test

## Global
* Tab Navigable
  - Move navigation bypass "skip to content" as the first tab (before logo)
  - Similar link to sitemap
  - Maybe a new sitemap or improvements / link to xml???
  - Similar link before the filter sidebar
* Wrap main content (`#primary`) with `<main role="main">` on every page in order to support skip to content links. Currently, any skip content goes to #main; include id if appropriate.
<!-- * [Remove title](http://a11yproject.com/posts/title-attributes/) -->
* Add `role="navigation"` to `<nav>`
* Add `role="banner"` to `<header>`
* Add `role="contentinfo"` to `<footer>`
* `#secondary` should be `<aside role="complementary">`
* Ensure site functionality (to checkout) is possible with Javascript disabled. While [most screen readers have JS enabled](http://a11yproject.com/posts/myth-screen-readers-dont-use-javascript/), we need to account for the 2% globally that doesn't.
  - Contact customer service number

## Product Listing page
  - "Skip to content" link triggers filter effect. Could we only include this on appropriate filters?
    - How does this affect screen readers location?
  - Remove `<h1>` from breadcrumbs

## Product Display Page
* Alt tags
  - Remove random commas & erratic size etc. (", , medium") from active large image
  - Give each variant a unique alt. Example: 'Side view of [product.name]', 'Top view of [product.name]', '360 View of [product.name], etc.
  - All decorative images (feature icons) should have alt=""
  - Small product images should say something like "View [side of [product.name]]"
  - Title should say "Click to zoom image"
* Add `role="tooltip"` to `.qtip-content` (image hover and "Add to cart" hover if no options selected). Advice if there is a more appropriate solution for screen readers
  - Perhaps include the "Add to cart" tooltip as an inline error to make more apparent & accessible

## Checkout Flow
* Ensure inline errors on forms. Many already do this and others highlight in red, but color impaired people need another indication.
* Add a format suggestion on phone field
* Forms should have labels and/or aria-label

## Styling
Part of the inspiration for creating this documentation is to create consistency and efficiency among those who work on the websites. There are five Front End Developers at Rocky Brands that need to better interact with the style sheets on each of the sites. I would like to explore a shared (perhaps with git?), basic style sheet and subsequent sheets for each brand to which all parties have access. There is a disconnect which causes conflicting definitions that make it slightly frustrating to update or create new content, but more importantly affects the performance and user experience of the websites through impacted load times or jarring [jank](http://jankfree.org/). This may be part of a larger future project.

While a global base + subsequent brand sheet would be great, sheets that loads only on PLP, PDP, and checkout flow would be great. An alternative to this solution would be to include content slots for those types of pages.

## Javascript
The same performance impact is shared with the scripts as with the css.

## Other
* Minicart should stay visible on hover
* Context changes (popups)
* Remove duplicate IDs (assess with tool of choice such as [this Chrome plugin](https://chrome.google.com/webstore/detail/dup-id-scans-html-for-dup/nggpgolddgjmkjioagggmnmddbgedice?hl=en-US))
* Images that link out or behave differently should indicate so w/ title and ARIA
* Icons and other critical elements should include alternative descriptors
* 14pt = 18px require 3:1 contrast ([measureable here](http://leaverou.github.io/contrast-ratio/))
  - Smaller requires 4.5:1 contrast
* Ensure context to buttons and other elements
* Responsive / support scale 200%
* All pages require alternative method to access; sitemap, search

* Ensure text over images are HTML
* Buttons have title attributes to describe behavior & helper info on hover
* Popup CTA focuses; esc. to close
* User [ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA) where appropriate
