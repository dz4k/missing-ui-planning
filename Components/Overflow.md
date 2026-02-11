---
Implemented: false
ARIA:
core: false
Form-associated: false
type: mixin
Time estimate (days): 10
Confirmed: true
---
- A row of items, such that any element that doesn’t fit in the row and would cause it to wrap or overflow will be moved into a separate container (the pane). The pane would usually be the body of a disclosure.
- TBD: Is it OK to require items to be direct children of the overflow? Otherwise, how should wrappers behave when their descendant items are moved into the pane?
- Should we duplicate wrappers in the pane? Should we remove them from the overflow when all their children are moved into the pane (and vice versa)?