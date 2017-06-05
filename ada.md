---
layout: page
title: ADA Compliance Requirements
description: Required action items for PFS web
---
## PFS web

The following are required changes to the current templates in order to comply with ADA AA requirements.

### Global
* Tab Navigable
  - Move navigation bypass "skip to content" as the first tab (before logo)
  - Add a similar, visually hidden link to sitemap
  - Improve sitemap
  - Similar link before the filter sidebar
* Wrap main content (`#primary`) with `<main role="main">` on every page in order to support skip to content links. Currently, any skip content goes to #main which doesn't exist on some pages. Category pages have <div id="main" role="main">: instances like this should be given the html5 "main" markup and all other rendering templates should wrap the content (slots) with the same.
<!-- * [Remove title](http://a11yproject.com/posts/title-attributes/) -->
* Add `role="navigation"` to `<nav>`
* Add `role="banner"` to `<header>`
* Add `role="contentinfo"` to `<footer>`
* `#secondary` should be `<aside role="complementary">`
* Ensure site functionality (to checkout) is possible with Javascript disabled. While [most screen readers have JS enabled](http://a11yproject.com/posts/myth-screen-readers-dont-use-javascript/), we need to account for the 2% globally that doesn't.
  - A potential alternative solution would be to show the customer support number and recommendation to contact us.
* When address is selected or other PDP parameter, the area reloads and restarts tab navigation

### Images
* Navbar: Flag by "Change country" should include alt text "[country name] Flag"
* Quickview: video image alt (or title if changing from image) should say "Open in pop out window / modal"

### Product Listing page
  - "Skip to content" link triggers filter effect. Could we only include this on appropriate filters?
    - How does this affect screen readers location? Ideally they should stay at their current location if selecting a filter or other 'sort' function.
  - Remove `<h1>` from breadcrumbs

### Product Display Page
* Alt tags
  - Remove random commas & size etc. (", , medium") from active large image
  - Give each variant a unique alt. Example: 'Side view of [product.name]', 'Top view of [product.name]', '360 View of [product.name], etc.
  - All decorative images (feature icons) should have alt=""
  - Small product images should say something like "View [side of [product.name]]"
  - Image alt text should say "Click to zoom image"
  - 360 Image alt text should say "Click and drag to rotate"
  - [Avoid title attributes](https://www.paciellogroup.com/blog/2013/01/using-the-html-title-attribute-updated/)
* Add `role="tooltip"` to `.qtip-content` (image hover and "Add to cart" hover if no options selected). Advise if there is a more appropriate solution for screen readers.
  - Perhaps include the "Add to cart" tooltip as an inline error to make more apparent & accessible

### Checkout Flow
* Ensure inline errors on forms. Many already do this and others highlight in red, but color impaired people need another indication (text).
* Add a format suggestion on phone input field &amp; [type="tel"](http://caniuse.com/#search=tel)
* Email should be type="email"
* Forms should have labels and/or aria-label
* Order summary page skips print receipt on tab navigation, needs addressed

### Styling
Part of the inspiration for creating this documentation is to create consistency and efficiency among those who work on the websites. There are five Front End Developers at Rocky Brands that need to better interact with the style sheets on each of the sites. I would like to explore a shared (perhaps with git), basic style sheet and subsequent sheets for each brand to which all parties have access. I'm not sure how / if this is possible, but I imagine having the ability to push a stylesheet to a bitbucket / github repository that would replicate to a dev instance (or staging) immediately and subsequently replicate to production over night.

There is a disconnect which causes conflicting definitions that make it slightly frustrating to update or create new content, but more importantly affects the performance and user experience of the websites through impacted load times or jarring [jank](http://jankfree.org/). This workflow improvement would allow for the usage of SASS, version control, and help productivity and site performance. This may be part of a larger future project, but want to raise awareness.

While a global base + subsequent brand sheet would be great, sheets that loads only on PLP, PDP, and checkout flow would be a nice further separation.

An alternative solution to this proposal would be to have unique content slots in the <head> of each type of page (or fix PDS's broken implementation).

### Javascript
The same performance impact and suggested workflow is shared with the scripts as with the css.

### Modals
* Popup modals [need to be described](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_dialog_role) for visually impaired users, including at least:
  - QuickView
  - Gift with purchase popup

```html
<div role="dialog" aria-labelledby="dialog1Title" aria-describedby="dialog1Desc">
  <h2 id="dialog1Title">Your personal details were successfully updated</h2>
  <p id="dialog1Desc">You can change your details at any time in the user account section.</p>
  <button>Close</button>
</div>
```

### Other
* Minicart should stay visible on hover
* Context changes (popups)
* Remove duplicate IDs (assess with tool of choice such as [this Chrome plugin](https://chrome.google.com/webstore/detail/dup-id-scans-html-for-dup/nggpgolddgjmkjioagggmnmddbgedice?hl=en-US))
* Quickview tab navigation is interrupted after selecting a variant
* Images that link out or behave differently should indicate so w/ [their alt text](http://a11yproject.com/posts/alt-text/) and / or ARIA
* Icons and other critical elements should include alternative descriptors
* 14pt = 18px require 3:1 contrast ([measureable here](http://leaverou.github.io/contrast-ratio/))
  - Smaller requires 4.5:1 contrast
* Ensure context to buttons and other elements
* Responsive / support scale 200%
* All pages require alternative method to access; sitemap, search
* Buttons have title attributes to describe behavior & helper info on hover
* Use [ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA) where appropriate
* [Add clip attribute](http://a11yproject.com/posts/how-to-hide-content/) to .visually-hidden class
* Ensure text over images are HTML
