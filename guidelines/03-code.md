---
layout: page
group: guidelines
permalink: /guidelines/code.html
title: Code conventions
description: Guidelines for the design system's code base.
---
Writing HTML, CSS, and Javascript in a cohesive and consistent structure is the goal so any current and future code maintainers can easily understand and continue development on the project. The below are standards that are highest priority - primarily relative to ADA compliance with external resources for a more granular understanding of best practices.
<!-- Check out the [Frontend Guidelines Questionnaire](https://github.com/bradfrost/frontend-guidelines-questionnaire) and [CSS Architecture for Design Systems](http://bradfrost.com/blog/post/css-architecture-for-design-systems/) for inspiration. -->
## HTML

### Markup
Markup should be written with semantic and meaningful HTML5 syntax so both users and search engines can access the site with reasonable limitations.

`<header role="banner">` A region of the page that is site focused. Typically your global page header.

`<nav role="navigation">` Contains navigational links.

`<main role="main">` Focal content of document. Use only once.

`<article role="article">` Represents an independent item of content. Use only once on outermost element of this type.

`<aside role="complementary">` Supporting section related to the main content even when separated.

`<footer role="contentinfo">` Contains information about the document (meta info, copyright, company info, etc).

`<form role="search">` Add a 'search' role to your primary search.

* Use semantic headings and structure
* Provide a "Skip to main content" link &amp; include a main section
* Content images should use `alt=""` if decorative, otherwise describe the function or description of the image

#### Forms

* Tab order of the form follows a logical pattern
* Each input / select, etc. should have an associated label
* Avoid using `placeholder` as a replacement for `label`
* Group related form elements with `fieldset` and describe the group with `legend`

## CSS
* Ensure links have `:focus` state for tabs
* Ensure links are recognizable (underlined)
* Show "Skip to main content" [on :focus](https://css-tricks.com/smooth-scrolling-accessibility)
* Occasionally audit your site with [Chrome Canary's devtool's code coverage](https://blog.logrocket.com/using-the-chrome-devtools-new-code-coverage-feature-ca96c3dddcaf) to see which styles are unused and reassess. A more actionable approach can be to [use UnCSS](https://github.com/giakki/uncss) to remove unused CSS.

### Javascript

* Never use inline scripting (separate functionality from structural markup)
* Provide alternatives for users who do not have Javascript enabled or is unavailable
* Occasionally audit your site with [Chrome Canary's devtool's code coverage](https://blog.logrocket.com/using-the-chrome-devtools-new-code-coverage-feature-ca96c3dddcaf) to see which scripts are unused and reassess.
