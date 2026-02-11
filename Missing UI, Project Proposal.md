# Missing UI: a framework-agnostic, headless ~~components~~ behaviors library

## Project proposal

Develop a comprehensive collection of common UI widgets and behaviors in JavaScript, meant for use in HTML, that

- don’t expect the website author to use a particular framework or library,

- are small in terms of bandwidth,

- are headless (i.e. don’t include any styling by default) but have optional stylesheets with default styling,

- are implemented with simple and well documented code,

- are easy to use,

- have exemplary accessibility.

To be delivered:

- For each behavior:

  - A JavaScript library,

  - Optional CSS stylesheet,

  - Usage documentation,

  - Development documentation.

- A JavaScript library of DOM utilities, used to construct the components, published separately to let users create their own components.

  - General DOM manipulation functions

  - Setup/teardown for components/behaviors

- Example interfaces implemented using the library.

# Base behaviors

_Commentary: Some of these might be “marketed” as libraries all on their own honestly._

## Light dismiss

Can be composed with other components to “close” the component when the user clicks outside the element. What it means to “close” is defined by the child component.

## Focus group (polyfill)

[https://open-ui.org/components/focusgroup.explainer/](https://open-ui.org/components/focusgroup.explainer/). A group of focusable elements, between which focus is moved via arrow keys. For the purpose of tab navigation, these elements are parts of one whole. This behavior is a foundational building block for many other components, and will likely be implemented via the *roving tabindex* technique.

## Hotkeys

Composable behavior that adds keyboard shortcuts to an element. For an example, see the menus in table rows of [https://franken-ui.dev/examples/task](https://franken-ui.dev/examples/task) — each row has a hotkey to activate an option in the menu.

## Reorderable

A composable behavior that makes a component’s children reorderable by clicking and dragging. Needs research to figure out if this is possible to implement generically, or needs to be implemented within specific components.

## Hover preview

A card that appears when a card is hovered, showing a snippet of information from the linked page. Most existing implementations seem to be exclusive to visual usage – is it impossible to make this accessible?

## Overflow

A row of *items*, such that any element that doesn’t fit in the row and would cause it to wrap or overflow will be moved into a separate container (the *pane*). The pane would usually be the body of a disclosure.

TBD: Is it OK to require items to be direct children of the overflow? Otherwise, how should wrappers behave when their descendant items are moved into the pane? Should we duplicate wrappers in the pane? Should we remove them from the overflow when all their children are moved into the pane (and vice versa)?

# Widget behaviors

## Menu

A menu. Already partially implemented in Missing.js. Nested menus are not yet implemented.

## Menu button

A button that opens a menu. Already implemented in Missing.js.

## Tabs

Composite of *tablist*, *tabs* and *tab panels*. The tablist may be vertical or horizontal, which will affect keyboard interactions. Already partly implemented in Missing.js.

Initially, tabs would not have features like closing, selecting or reordering. However, a more advanced “browser-style” tabs component can be considered.

## Feed

An infinitely-scrolling list of items with keyboard shortcuts for access. Already implemented in Missing.js thanks to a contributor.

## Menubar

A horizontal menu of menus.

## Context menu

Opens a menu when its child is right-clicked.

## Combobox (searchable select)

A combination of a text input and a select menu. Allows searching through the allowable values by typing. [https://open-ui.org/components/combobox.explainer/](https://open-ui.org/components/combobox.explainer/).

## Sortable table

Table headers that can be clicked to toggle between states of “ascending”, “descending” and “none”. This component doesn’t actually sort the table (that would be done server-side), but it does manage the states of sort buttons and emit events for htmx to listen to, as well as exposing sort values as form data.

## Progress bar

Shows the ongoing progress of a long-running operation. Can have a percetage value, or no value if no estimate is available for how much of the operation is completed (this makes an *indeterminate* progress bar).

## Toolbar

An array of related interactive elements, presented in a row or column.

## Breadcrumbs

A control showing the position of the current page or view in a hierarchy. Each “crumb” can open a menu that shows other items on that level of the hierarchy.

## Chip input

Used to input a list of values, either from a preexisting list, or adding new values on the fly. The most common use case for this kind of input would be adding tags/categories.n

## Tree

“A `tree` is a widget that allows the user to select one or more items from a hierarchically organized collection.”

## Grid/list

See [https://react-spectrum.adobe.com/react-aria/GridList.html](https://react-spectrum.adobe.com/react-aria/GridList.html). For our purposes, a list that can be navigated via keyboard shortcuts like arrow keys.

## Card link

An article where clicking anywhere on the article (that isn’t itself clickable) activates a certain link or button or other action. This can be implemented in css (see “card pseudo element hack”), but a JS implementation would be composable with other components (e.g. a gridlist with cards could activate the cards).

## Toast

A notification that usually disappears on its own.

## Toggle button

A button that can be “pressed down”, e.g. a play-pause button. Different from checkboxes and switches… somehow. Already implemented in Missing.js.

## Toggle button group

A series of toggle buttons, e.g. bold/italic/underline or flush-left/flush-right/centered/justified. Can be exclusive or multi selectable.

## Customizable select

[https://open-ui.org/components/customizableselect/](https://open-ui.org/components/customizableselect/) explains a proposal for a customizable implementation of the \<select\> element, including rich content being allowed in options. This component would serve as a polyfill for that functionality, reimplementing the select element in JS and ARIA.

## Date picker

A component to select a date from the Gregorian calendar. TBD: support for other calendars, localization support.

### Date range picker

Select two dates that define a span of time.

# Excluded components

**Checkbox:** Present in Radix and React Aria, on the basis that HTML-native checkboxes (`<input type=checkbox>`) are hard to style. Obsoleted by advances in CSS, e.g. `appearance: none`. 

**Switch:** Just a checkbox with role `switch` and styling. Default styles could be added for `<input type=checkbox role=switch>` in Missing.css.

**Dialog:** Natively available in HTML as `<dialog>`.

**Popover:** Soon to be natively available in HTML as the `popover` attribute.

**Accordion:** Natively available in HTML via `<details>` with `name` attribute.

# General requirements

Components should mutate their child elements as little as possible. They should be able to initialize themselves when the children have already been mutated (i.e. if a live DOM tree is stringified and restored, such as during htmx history restoration).

Components should emit events liberally for interactions performed on them, so that their behavior can be hooked into.

Styles (that are not strictly required for functionality) should be published in a CSS stylesheet (rather than being embedded in the component, or requiring a dependency like Tailwind). The components should be fully usable without the stylesheet, i.e. users should be able to write their own stylesheets instead.

Use of Shadow DOM should be avoided, completely if possible. This is to avoid problems in integrating with other libraries, particularly htmx.

# Non-functional requirements

**Distribution.** All components will be distributed as a single package, on [npm](https://npmjs.com). They will be developed in a Git repository owned by Big Sky Software.

**Accessibility.** All components will be conformant with WCAG 2.2 and tested for keyboard, touch, and screen reader usage.

**Interface.** Programmatic interactions with (and between) components should take place through DOM events, rather than functions or callbacks. (see [Gross et al. 2023 *Hypermedia Systems*, ch. 09 “Client Side Scripting”, sec. “Integration Options”](https://hypermedia.systems/client-side-scripting/#_integration_options)).

When reasonable, the user should set ARIA attributes to provide arguments to a behavior, rather than using custom attributes to pass arguments and the component setting those ARIA attributes.

TBD: use the `invokeaction` / `invoketarget` attributes that are being discussed for standardization?

**Architectural style.** Adhere to [rsjs](https://ricostacruz.com/rsjs/) and [rscss](https://ricostacruz.com/rscss/) conventions. Follow style of readily implemented Missing.js components.

Avoid component states that are not reflected in the DOM.

# Project background

The Missing.css library styles elements based on ARIA roles. This convention was adopted for the sake of brevity (not requiring the user to specify both a class and a role), and encouraging correct ARIA use (by making it required to get styling). However, many roles have requirements around interactive functionality, which CSS could not provide (checkbox hacks notwithstanding). This could be seen in earlier versions of Missing.css documentation, which included non-functional tabs and menus. The documentation disclaimed that “JS \[was\] sold separately”, but this was merely a band-aid on a bullet hole, since requiring use of ARIA to get styling without providing an easy way to implement the associated behavior would encourage inaccessible UI development. For this reason, [Missing.css 1.0.0](https://missing.style/releases/1.0.0/) introduced *missing.js*, a small set of components that would be the “code-behind” for Missing’s ARIA components.

Today, many developers use UI toolkits like [Radix UI](https://www.radix-ui.com/) \[TODO: add more examples\] to get common widgets to use in their apps. However, all these libraries have at least some of these disadvantages:

1. They are coupled to a SPA framework (usually React) (Radix, React Aria)

2. They require copying large amounts of code, sometimes duplicating code when the same component is reused (Tailwind UI, Alpine UI Components)

3. They have built-in styling, making them a nonstarter for sites that need bespoke styling, and contributing to the perception among users that “all websites look the same these days” (Radix, Tailwind UI)

Missing.js was a proof-of-concept for a component library without these drawbacks. Missing UI will build on Missing.js to create a comprehensive UI toolkit.