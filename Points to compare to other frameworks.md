## Framework-free
Does not require a framework like React, Vue, Alpine etc. Record the dependencies of the library, incl. frameworks and things like Tailwind

## Framework-independent
Does not require the _user_ to use a framework, even if one was used internally.

## Headless
Components have no built-in-styling other than what's functionally necessary.

## Has styles
Has default styling for components (optional if headless).

## Classless
If styles are provided, they can be applied to an HTML document without adding any classes.

## Styleable
The appearance of components can be customized. Has three states:
- Unstyleable -- no customization other than basic variants and configuration
- Config-styleable -- somewhat customizable by setting config options or CSS variables defined by the developers (sometimes called "design tokens")
- Fully styleable -- can be styled with the full power of CSS, no restrictions caused by bespoke theming systems or shadow DOM

## Buildless
Does not require a build system, JS bundler or npm. Can be vendored as simple JS files.

## Meant for real-world usage
i.e. doesn't have a "not for production" disclaimer like the WAI-ARIA APG example impls.