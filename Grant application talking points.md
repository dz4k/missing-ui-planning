# Missing UI -- Arguments for grant applications

**Missing UI is a class-light CSS library plus a set of well-implemented, well-tested UI components.** OK, so are a lot of other projects. But Missing fits a specific set of requirements:

- **Framework-agnostic:** the user does not need to use a specific UI framework like React. The components are maximally resilient to DOM manipulations they do not control, so they won't be broken by frameworks doing "creative" things.
- **Framework-free:** no framework is used internally as a dependency either -- we have our own femto-frameworks, 19.js and 43.js
- **Headless:** The JS components can be used without the CSS stylesheet. Styles that are mandatory for functionality or usability (e.g. hiding closed menus, laying out toolbars in the correct orientation) are applied programmatically. Visual styles are written in a plain-vanilla CSS stylesheet.
- **Classless:** The CSS stylesheet can be applied to a plain-HTML document and generate a pleasant result.

## Improve non-SPA sites.

A "traditional" website that doesn't use a SPA framework like React or Vue will have a hard time using UI libraries built for/with these frameworks.

Standards-based component libraries exist, such as Web Awesome, often relying on Custom Elements/Web Components, but these are rarely headless.

This leaves the majority of web developers with few options when they need a widget not included in HTML, such as tabs or a combobox:

1. **Use "headed" component libraries.** These offer a generic look-and-feel at best. At worst, they are design systems of other organizations, imbued with their branding, open-sourced for various reasons. Styling them often involves JS, or CSS variables; in each case, styling is limited by the interface the component developers choose to expose.

2. **Use independent libraries for each component.** Such libraries are often bloated with unneeded functionality to justify their existence. Likely created before the dominance of React-likes, many bring a jQuery dependency and outdated approaches -- more bloat obviated by modern Web standards.

	Each library brings
	- duplicated functionality, leading to code bloat and low performance),
	- "creative" DOM manipulation (especially in older libraries) leading to unforeseen interactions between libraries, thus bugs
	- Disjointed look-and-feel
	- Inconsistent coding patterns from distinct API designs (again, more common in older libraries)

3. **Create their own ad-hoc implementations.** The creation of these components is usually a prerequisite for other site development tasks, so they are often rushed. "Minimum-viable" widgets are undertested, and far too many developers consider inaccessible UI "viable".

4. **Create their own design system and component library.** A massive time and labor investment, requiring specialists to do properly, and with lots of work duplicated from organization to organization.

The availability of a comprehensive component library fitting our constraints would give web developers the most flexible option. We want the non-React majority to be able to have their cake and eat it too. To be able to design their sites freely, without having to make decisions that should have already been made. **We want to make usablility usable, performance fast, accessibility accessible.**


## Advancing the Web Platform

**Missing UI will advance the Open UI project by providing real-world implementations of new UI patterns.** Open UI already studies existing design systems, 25 are listed on their website. [I'm having trouble selling this one. What makes ours special?]