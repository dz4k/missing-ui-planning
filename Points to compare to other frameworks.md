
## Component count
Approximate.

## Framework-free
Does not require a framework like React, Vue, Alpine etc. We record the dependencies of the library, incl. frameworks and tools like Tailwind.

## Framework-independent
Does not require the _user_ to use a framework, even if one is used internally.

## Headless
Components have no built-in-styling other than what's needed for functionality.

## Has styles
Has default styling for components (optional if headless).

## Classless
If styles are provided, they can be applied to an HTML document without adding any classes.

## Styleable
The appearance of components can be customized.
- Unstyleable -- no customization other than basic variants and configuration
- Config-styleable -- somewhat customizable by setting config options or CSS variables defined by the developers (sometimes called "design tokens")
- Fully styleable -- can be styled with the full power of CSS, no restrictions caused by bespoke theming systems, shadow DOM or built-in styles taking priority

## Buildless
Does not require a build system, JS bundler or npm. Can be easily downloaded and vendored.

## Writing modes support
Components should work well in right-to-left languages, and ideally vertical scripts as well. Frameworks rarely document this, so we used the test of placing the [[Tablist|tab list component]] in a container element with the attribute `dir="rtl"` and checking that moving between tabs with arrow keys works correctly, with the left arrow moving left (next tab) and the right arrow key moving right (previous tab).
