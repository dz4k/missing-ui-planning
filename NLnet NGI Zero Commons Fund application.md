::::
Filling out [this form](https://nlnet.nl/propose/).
::::

**Thematic call**
NGI Zero Commons Fund

**Contact information**
Deniz Akşimşek
deniz@aksimsek.tr
+90 533 375 13 29
Organization: N/A
Turkey

**General project information**
Proposal name
Missing UI
Website
https://missing.style

**Abstract**
Currently, Missing.css is a CSS library with a few JS widgets. The proposed project is to create a comprehensive UI component library with implementations for any common UI pattern not included in HTML. Our goal is widgets that are - framework independent, - tooling independent (e.g. not requiring npm or a bundler), - simple and well-documented code, - "headless" and freely styleable, - with optional pre-made styling, - exemplary in usability and accessibility, - comprehensively tested. We will also publish a utility library that we use in the implementation of these components. Our mission is to allow rapid development of web interfaces, and improve the usability and accessibility of the silent majority of websites that do not use SPA frameworks. Our stretch goal is to drive web UI standards forward by working with efforts like Open UI (https://open-ui.org).

**Have you been involved with projects or organisations relevant to this project before? And if so, can you tell us a bit about your contributions?**

I was commissioned to build Missing 1.0 by Big Sky Software (MT, US) and Commspace (RSA). I have been maintaining it ever since. I was eventually joined by Geoffrey Eisenbarth, who used the library at his workplace and made huge contributions. I created the vision for Missing 2.0 / Missing UI and was in talks with a potential sponsor, but did not continue as they requested changes that would couple the component library to their in-house framework. Instead, I shared it with Geoff -- we have been working on it ever since.

**Explain what the requested budget will be used for? Does the project have other funding sources, both past and present? A breakdown in the main tasks with associated effort is appreciated. Make rates explicit.**
The first version of Missing.css was commissioned by Big Sky Software (MT, US) and Commspace (RSA), who paid a total of 4000 USD. All development after the 1.0 release has been unfunded, however, my co-maintainer Geoff works on the project during his work hours.

After starting work on Missing 2.0/Missing UI, we found that the degree of diligent usability and accessibility testing required for the massive increase in scope of our project does not easily fit into after-hours or downtime at another job. Thus, if the funds are granted, I will start working on Missing.css full-time.

We would also like to acquire a Mac mini for testing on Safari (and iOS Safari via simulator). We are evaluating options like BrowserStack, however.

Costs:
- Labor (estimated, see breakdown in full budget):
	- Days: 112
	- Day rate: 80 EUR
	- Total: 8960 EUR
- Apple Mac Mini (for testing on Safari): 550 EUR
- Polypane subscription: 72 EUR (12 * 6 months)
Total: 9582 EUR

Our time estimates are optimistic, so the project may extend beyond the planned 6 business months, but is unlikely to stretch close to a year. 

**Compare your own project with existing or historical efforts.**
Missing UI will distinguish itself by combining all of the below features:
- Framework-independent vs. Radix UI, shadcn, Headless UI, React Aria...
- Framework-free vs. Franken UI, Vaadin...
- Headless vs. Web Awesome, Crayons, Vaadin, Spectrum WC...
- Freely styleable via plain CSS (as opposed to configuration-driven styling) vs. Fluent UI, Chakra UI
- With optional pre-made styles, vs. u-elements, 
- With optional classless styling, vs. all libraries examined,
- Not requiring frontend tooling (including bundlers, npm, and special CLIs) vs. Agnostic UI
- Exposing its own composable building blocks, like the FocusGroup mixin
- Meant for real-world usage vs. WAI-ARIA APG example implementations

We have attached a detailed feature matrix comparing various existing component libraries. The majority are:
- Specific to a framework like React or Vue,
- A company's branded design system that just happens to be open-sourced,
- Prevent direct styling (e.g. by using Shadow DOM heavily), and expose limited customization hooks

u-elements is the closest 

It is my feeling that most existing UI frameworks presume _developers_ as the target audience, and optimize for solving the web author's problems -- only focusing on the end user insofar as the developer does. This is not the approach we will take. In accordance with the W3C Priority of Constituencies, we plan to optimize for the _web user_, looking to improve the usability and accessibility of web applications as a whole. To the extent that we cater to developers, it will be to drive adoption (expanding impact area), and relieve "footguns" that lead to both broken websites and developer misery.

**What are significant technical challenges you expect to solve during the project, if any?**
- Performing extensive usability and accessibility testing and working around browser and AT bugs. Testing, debugging and "UI sanding"[^1], as opposed to the initial implementations of each component, will contribute most to our goals of accessibility and resilience, and is my main motivation for seeking out funding.
- Achieving and testing for "DOM resilience", i.e. other libraries manipulating DOM or elements being serialized to HTML and revived should not break Missing UI.
	- Achieving DOM resilience is likely to require heavy use of the IntersectionObserver API. This is known to have performance drawbacks [TODO link to caleb porzio blog post]. Testing and optimization will be needed to make sure using Missing UI components doesn't degrade the performance of a website.
- Using newly available web APIs where best practices have not yet arisen. Interpreting complex Web platform specs and drafts to ensure our work is conformant with current and future specs, and follows the "grain" of the platform.
- Creating abstractions like FocusGroup that can generalize logic across many components, but remain flexible enough for the sorts of edge-case handling good UI usually requires.
- Developing polyfills when needed.
- Remaining maximally consistent with native platform behavior when that behavior varies across devices, and browsers don't always expose the necessary APIs.

[^1]: https://blog.jim-nielsen.com/2024/sanding-ui/


**Describe the ecosystem of the project, and how you will engage with relevant actors and promote the outcomes?**
The project currently targets personal sites and small organizations as users. Missing UI is a massive increase in scope, and achieving our vision will require adoption across a broad range of websites.

Missing is closely linked with the htmx (https://htmx.org) community and is hosted under the same Big Sky Software GitHub organization. We plan to promote Missing UI as a companion library for client-side interactions not easily implementable with htmx. We will consider setting up separate sponsorship infrastructure for Missing, as we do not benefit from Big Sky sponsors except for website hosting and domain registration.

[TODO: ask hypersys team about this!!!] I am also a co-author of Hypermedia Systems, a book which uses Missing 1.0 as a simple stylesheet in an example software project (Contact.app). A future edition of Hypermedia Systems may include a chapter on using the newly implemented components.

**Attachments**
We had that old "Missing UI Project Proposal" document -- maybe we should update that with the current component list and attach it.
