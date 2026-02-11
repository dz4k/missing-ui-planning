---
Implemented: false
ARIA: ""
core: false
Form-associated: false
type: tag
Dependencies: []
Time estimate (days): 10
Confirmed: false
---

An element with role `button`. Wraps an input, hides it from the accessibility tree and prevents it being focused. When clicked, reveals and focuses the input. The input can be closed with `Esc`, returning focus to the button.

Should ideally proxy key events not handled by a parent focusgroup to its child.

Used for putting inputs in toolbars, to give the user control over whether key events are  handled by the input or focusgroup. Prevents getting "trapped" in an input when navigating a focusgroup with arrow keys, or getting "kicked out" of an input when trying to use arrow keys for editing.