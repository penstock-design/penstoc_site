## Where Planning and Strategy Come From

Before page building begins, a significant amount of **planning and thinking work** has already happened. This work produces the inputs that feed into the Penstock Page‑Building Model.

This planning does **not** happen in code, and it should not be solved with HTML, CSS, or JavaScript.

Think of this as the **context layer** for page building.

---

## Planning Inputs You Should Expect

These inputs can vary widely in quality, completeness, and format. That is normal. The goal at this stage is **clarity**, not polish.

### 1. Client Information

This includes:

* notes from calls or meetings
* emails and messages
* questionnaires or intake forms
* stated goals, constraints, and priorities

This information explains *why* the site exists and what success looks like.

---

### 2. Content Documents

Often one or more long documents containing:

* page‑by‑page copy
* rough drafts mixed with final text
* headlines, body copy, and calls to action

These documents answer:

* What are we saying?
* What information must exist on each page?

They do **not** define layout or HTML structure.

---

### 3. Media Assets

Media inputs may include:

* images
* videos
* logos
* brand assets

Quality and organization will vary.

Media exists to **support content**, not dictate structure.

---

### 4. Site Plan (Site Architecture)

This may exist as:

* a text outline
* a diagram
* a sitemap

It defines:

* what pages exist
* how pages relate to each other
* what belongs in navigation

This is **site‑level structure**, not page‑level structure.

---

### 5. Content Architecture (Information Grouping)

This work answers:

* which content belongs on which page
* what content repeats across pages
* what content supports decisions

This is about **information placement**, not visual design.

---

### 6. Wireframes (Any Fidelity)

Wireframes may be:

* rough sketches
* low‑fidelity layouts
* polished mockups

Wireframes suggest:

* grouping of content
* rough order of sections

They are **advisory**, not instructions for markup.

---

## How These Inputs Feed Page Building

By the time page building begins, you should already know:

* what pages exist
* the purpose of each page
* what content belongs on the page
* a rough idea of section order

Page building starts only after this context is understood.

---

# Doc 00 — The Penstock Page‑Building Model

## Purpose of This Document

This document defines **how pages are built** inside the Penstock framework.

It is not about visual design.
It is not about tools.
It is not about clever techniques.

It exists to:

* keep page building calm and predictable
* reduce decision fatigue
* prevent messy, fragile markup
* give you a repeatable way to think through any page

If something feels wrong while building a page, this model helps you identify *where* the problem is — before you start “fixing” things with CSS or JavaScript.

---

## What This Model Is (and Is Not)

This model is:

* a **thinking framework** for building pages
* focused on **HTML, CSS, and light JavaScript**
* suitable for static marketing sites

This model is **not**:

* a visual design system
* a JavaScript architecture
* a framework replacement

Astro is the delivery tool. This model is how you decide *what* to deliver.

---

## High‑Level Overview

Page building in Penstock is organized into **layers of responsibility**.

Each layer has a clear job.
Each layer must not do the job of another.

The layers are:

1. Strategy *(pre‑build)*
2. Systems
3. Structure
4. Semantics
5. Selectors
6. Styling
7. Scripting

These layers are applied **in order**.

---

## 0. Strategy (Pre‑Build)

**Strategy happens before any code is written.**

Strategy answers:

* Who is this page for?
* What must the visitor understand?
* What action matters most?

Strategy lives outside the codebase:

* briefs
* notes
* outlines

Rules:

* Strategy is required before page building begins
* Strategy is never solved with CSS or JavaScript
* If structure feels unclear, revisit strategy

Strategy informs page building, but it is **not part of page construction itself**.

---

## 1. Systems

**Systems are the rules that already exist before a page is built.**

Systems include:

* naming conventions
* spacing scales
* typography scales
* component extraction rules
* accessibility guardrails
* folder structure

Systems:

* do not build pages
* do not decide content
* do not add visuals

Their role is to:

* remove repeated decisions
* keep pages consistent
* protect good choices over time

In Penstock, the framework itself *is* the Systems layer.

---

## 2. Structure

**Structure defines what exists on the page and in what order.**

Structure answers:

* What sections are on this page?
* What comes first, second, third?
* What is primary vs supporting?

Structure does **not** include:

* HTML tags
* CSS
* layout details

Examples of structure:

* site header
* navigation
* hero section
* services section
* call to action

If the page feels confusing or bloated, the problem is usually structure.

---

## 3. Semantics

**Semantics define what each thing is.**

This is where HTML is chosen.

Semantics answers:

* Is this a `header`, `main`, `section`, or `article`?
* Is this a `button` or a link?
* Does this content stand on its own?

Rules:

* HTML elements are chosen for meaning, not appearance
* Headings communicate structure, not size
* Accessibility begins here

CSS must never be used to compensate for poor semantics.

---

## 4. Selectors

**Selectors are how CSS and JavaScript find things.**

Selectors include:

* class names
* data attributes
* ARIA attributes

Selectors are:

* chosen deliberately
* simple and stable
* based on structure and meaning

Selectors are **not**:

* accidental DOM paths
* deeply nested chains
* tied to visual quirks

Selectors form the interface between:

* HTML
* CSS
* JavaScript

---

## 5. Styling

**Styling controls how the page looks and responds visually.**

Styling includes:

* spacing
* typography
* color
* layout behavior

Rules:

* styling reacts to structure and selectors
* styling does not introduce meaning
* styling does not control behavior

Styling is token‑driven and predictable.

If styling feels brittle, revisit selectors or structure — not more CSS.

---

## 6. Scripting

**Scripting adds behavior.**

Scripting is used when:

* HTML alone is not enough
* CSS alone is not enough

Examples:

* opening and closing a navigation menu
* toggling visibility
* updating simple state

Rules:

* JavaScript is planned during structure and semantics
* JavaScript is implemented after markup exists
* JavaScript changes state, not structure
* JavaScript remains small and isolated

Scripting supports the page — it does not drive it.

---

## The Build Order (Mental Checklist)

When building any page, think in this order:

1. Strategy — why this page exists
2. Systems — rules already in place
3. Structure — what exists and in what order
4. Semantics — what each thing is
5. Selectors — how styling and behavior attach
6. Styling — how it looks
7. Scripting — how it behaves

If something breaks, identify **which layer is responsible** before making changes.

---

## Why This Model Matters

This model:

* prevents div soup
* prevents CSS hacks
* keeps JavaScript small
* makes pages easier to return to months later

Most importantly:

> When something feels wrong, you don’t guess — you diagnose.

That is the goal of the Penstock Page‑Building Model.

---

## Naming (BEM‑Style) — How We Name Things So Future‑You Understands Them

Naming touches **Structure** and **Selectors**.

There is no universal “correct” naming system. The goal in Penstock is simpler:

* names should be **obvious when you come back months later**
* names should describe **what the thing is**, not how it looks
* names should be **consistent across pages**

### What We Use (Plain BEM‑Style)

We use a **BEM‑style pattern** because it’s predictable and readable:

* **Block**: a standalone UI chunk

  * example: `.service-card`, `.site-header`, `.hero`, `.nav`

* **Element**: a part inside a block

  * example: `.service-card__media`, `.service-card__title`, `.nav__list`

* **Modifier**: a variation of a block or element

  * example: `.service-card--featured`, `.button--primary`

We keep it “plain BEM‑style” (not strict or dogmatic). The goal is clarity, not purity.

### Naming Rules (Penstock)

**1) Name by meaning, not appearance**

* ✅ `.service-card__media`
* ❌ `.service-card__left`

**2) Prefer fewer, clearer names**

* A name should explain the part without reading the CSS.

**3) Avoid page‑specific naming inside reusable blocks**

* ✅ `.service-card__meta`
* ❌ `.homepage-services-card__meta`

**4) Use consistent words for common parts**
These terms should mean the same thing everywhere:

* `__media` (image/video/figure area)
* `__content` (text body)
* `__title` (heading inside a block)
* `__desc` (supporting text)
* `__actions` (buttons/links area)
* `__icon` (decorative or functional icon)
* `__list`, `__item` (lists)

**5) Use modifiers for variations, not new blocks**

* ✅ `.service-card--featured`
* ❌ `.featured-service-card`

### When a Wrapper Needs a Name (and When It Doesn’t)

Wrappers are normal. Not every wrapper needs a selector.

Give a wrapper a selector only when it has a real job:

* it needs spacing/layout styling
* it needs a state selector
* JavaScript needs to find it

If it has no job, prefer **no selector** (keep the HTML cleaner).

### Selectors vs Structure (Quick Reminder)

* **Structure** decides what parts exist.
* **Selectors** decide how CSS/JS find those parts.
* Naming is where those two layers meet.

---

## How This Document Is Used

This document is the **entry point** for all page building inside Penstock.

Every other page‑building document assumes:

* this model is understood
* this language is used
* these responsibilities are respected

Do not skip layers.
Do not collapse responsibilities.

Calm, clear pages are the result.

## Where Planning and Strategy Come From

Before page building begins, a significant amount of **planning and thinking work** has already happened. This work produces the inputs that feed into the Penstock Page‑Building Model.

This planning does **not** happen in code, and it should not be solved with HTML, CSS, or JavaScript.

Think of this as the **context layer** for page building.

---

## Planning Inputs You Should Expect

These inputs can vary widely in quality, completeness, and format. That is normal. The goal at this stage is **clarity**, not polish.

### 1. Client Information

This includes:

* notes from calls or meetings
* emails and messages
* questionnaires or intake forms
* stated goals, constraints, and priorities

This information explains *why* the site exists and what success looks like.

---

### 2. Content Documents

Often one or more long documents containing:

* page‑by‑page copy
* rough drafts mixed with final text
* headlines, body copy, and calls to action

These documents answer:

* What are we saying?
* What information must exist on each page?

They do **not** define layout or HTML structure.

---

### 3. Media Assets

Media inputs may include:

* images
* videos
* logos
* brand assets

Quality and organization will vary.

Media exists to **support content**, not dictate structure.

---

### 4. Site Plan (Site Architecture)

This may exist as:

* a text outline
* a diagram
* a sitemap

It defines:

* what pages exist
* how pages relate to each other
* what belongs in navigation

This is **site‑level structure**, not page‑level structure.

---

### 5. Content Architecture (Information Grouping)

This work answers:

* which content belongs on which page
* what content repeats across pages
* what content supports decisions

This is about **information placement**, not visual design.

---

### 6. Wireframes (Any Fidelity)

Wireframes may be:

* rough sketches
* low‑fidelity layouts
* polished mockups

Wireframes suggest:

* grouping of content
* rough order of sections

They are **advisory**, not instructions for markup.

---

## How These Inputs Feed Page Building

By the time page building begins, you should already know:

* what pages exist
* the purpose of each page
* what content belongs on the page
* a rough idea of section order

Page building starts only after this context is understood.

---

# Doc 01 — Structure: How Pages Are Assembled

## Purpose of This Document

This document explains **Structure** in the Penstock Page‑Building Model.

Structure answers one question only:

> **What exists on the page, and in what order?**

It does **not** decide:

* HTML tags
* CSS
* JavaScript

Those come later.

If a page feels confusing, bloated, or hard to edit, the problem is usually **structure**, not styling.

---

## What “Structure” Means in Practice

Structure is the **outline of the page**.

Think in terms of:

* sections
* sequence
* priority

Before writing any HTML, you should be able to describe the page like this:

* Header
* Hero
* Services overview
* Proof / credibility
* Call to action
* Footer

No visuals. No layout. Just parts and order.

---

## Structure Comes From Strategy

Structure is informed by strategy.

If strategy says:

* “clarity first” → hero comes early
* “comparison matters” → features appear before pricing
* “trust is the blocker” → proof appears before CTA

Then structure reflects that.

If you’re unsure where something belongs, revisit strategy — not CSS.

---

## Sections: The Core Structural Unit

A **section** is a conceptual grouping of content.

A section exists because:

* its content belongs together
* it communicates a single idea

Examples of sections:

* hero
* services
* testimonials
* FAQ
* call to action

Sections are **not** visual blocks.

They may look similar or different later — that is a styling concern.

---

## The “Section + Container” Pattern

Penstock uses a consistent structural pattern:

* an outer **section**
* an inner **container**

Why:

* the section controls vertical rhythm and spacing
* the container controls content width

This pattern:

* keeps layouts predictable
* prevents repeated width logic
* makes responsive behavior easier later

At the structure stage, this is just a rule — not CSS.

---

## Page‑Level Structure (Example: Homepage)

A typical homepage structure might look like:

* Site header
* Hero section
* Services section
* Proof section
* Call to action section
* Site footer

At this stage:

* no class names
* no HTML tags
* no styling assumptions

Just the outline.

---

## Header and Navigation Structure

The site header is a **distinct structural region**.

Conceptually, it contains:

* site identity (logo/name)
* primary navigation
* optional primary action

Important structural rules:

* header is separate from hero
* navigation is grouped as one unit
* dropdowns are noted as **interactive needs**, not behaviors

Structure can acknowledge interaction without implementing it.

---

## Hero Structure

The hero is the **first major content section**.

Structurally, it often includes:

* primary heading
* supporting text
* primary action
* optional secondary content (image, trust signal)

The hero exists to:

* orient the visitor
* communicate value quickly
* lead into the rest of the page

Visual size and layout are not structural concerns.

---

## Repeating Structures (Lists and Cards)

When content repeats, structure matters even more.

Examples:

* service cards
* feature lists
* testimonial items

Structure decisions include:

* is this a list of items?
* does each item stand alone?
* what parts does each item have?

This is where you decide things like:

* card
* media area
* content area
* actions area

Naming and selectors come later — structure comes first.

---

## Structure Before Reuse

Do **not** jump straight to components.

First:

* build the structure once
* confirm it makes sense
* confirm it repeats

Only then do you extract reusable components.

Structure before reuse keeps components simple and flexible.

---

## Common Structure Mistakes

**Mistake: designing structure visually**

* “This looks like two columns”

Fix:

* identify the conceptual sections first

---

**Mistake: skipping sections**

* everything dumped into one large section

Fix:

* split content by idea, not by appearance

---

**Mistake: letting CSS dictate structure**

* adding wrappers only to make layout work

Fix:

* define structure first, then style it

---

## Structure Checklist

Before moving on to Semantics, confirm:

* You can describe the page as a clear list of sections
* The order supports the page’s goal
* Each section has a reason to exist
* Repeating content has a consistent internal structure

If any of these fail, fix structure before continuing.

---

## What Comes Next

Once structure is locked:

* choose correct HTML elements (Semantics)
* then decide how CSS and JS will target parts (Selectors)

Structure is the foundation.

If it’s solid, everything else gets easier.

# Doc 02 — Semantics: Choosing the Right HTML Elements

## Purpose of This Document

This document explains **Semantics** in the Penstock Page‑Building Model.

Semantics answers one core question:

> **What is each thing on the page?**

This is about choosing the **right HTML elements for meaning**, not appearance.

Good semantics:

* make pages easier to understand
* improve accessibility automatically
* reduce the need for JavaScript fixes later

Poor semantics lead to:

* confusing markup
* fragile CSS
* accessibility problems

---

## Semantics Comes After Structure

Semantics is applied **after Structure is clear**.

You should already know:

* what sections exist
* what order they appear in
* what content belongs together

Semantics does **not** decide:

* layout
* spacing
* visual style

Those come later.

---

## Page Landmarks (The Big Regions)

Landmarks describe the **major regions of a page**.

They help:

* screen readers
* keyboard navigation
* humans reading the markup

Use these landmarks intentionally.

### `header`

Use for:

* site headers
* page headers
* section headers (when appropriate)

Do not use `header` just for styling.

---

### `nav`

Use for:

* primary navigation
* secondary navigation

Rules:

* navigation links should live inside `nav`
* avoid putting non‑navigation content inside `nav`

---

### `main`

Use for:

* the primary content of the page

Rules:

* only one `main` per page
* `main` should not be inside `header`, `nav`, or `footer`

---

### `footer`

Use for:

* site footer content
* section‑level footers (when meaningful)

Do not use `footer` just to push content to the bottom.

---

## Sections and Grouping Content

### `section`

Use `section` for:

* a thematic grouping of content
* content that has a clear topic

Rules:

* sections should usually have a heading
* do not use `section` purely as a wrapper

---

### `article`

Use `article` for:

* standalone, reusable pieces of content

Examples:

* service cards
* blog posts
* testimonials

Rule of thumb:

> If the content could be moved or reused independently, consider `article`.

---

### `div`

Use `div` when:

* no semantic element fits
* the element exists only for grouping or styling

`div` is not bad — it is neutral.

---

## Headings (Structure Signals)

Headings communicate **document structure**, not visual size.

Rules:

* use one `h1` per page (usually in the hero)
* headings should follow a logical order (`h2`, `h3`, etc.)
* do not skip heading levels for visual reasons

Headings help both users and assistive technology understand the page.

---

## Links vs Buttons (Critical Distinction)

This is one of the most important semantic decisions.

### Use a link (`a`) when:

* clicking navigates to another page
* clicking changes the URL

---

### Use a button (`button`) when:

* clicking triggers an action
* clicking changes state (open/close, show/hide)
* clicking does not navigate

Do **not** fake buttons with links or vice versa.

This decision prevents many accessibility and JavaScript issues.

---

## Lists

Use lists when content is a list.

### `ul` / `ol`

Use for:

* navigation items
* feature lists
* steps

Do not use lists just for indentation.

---

## Media and Figures

### `figure`

Use `figure` when:

* media is part of the content
* media may have a caption

### `figcaption`

Use for:

* captions that describe the media

---

## Forms and Inputs (High Level)

Use semantic form elements:

* `form`
* `label`
* `input`
* `textarea`
* `button`

Rules:

* every input should have a label
* placeholders are not labels

Form behavior can be enhanced later with JavaScript.

---

## Semantics and Accessibility

Good semantics provide:

* keyboard access by default
* screen reader support
* predictable behavior

Accessibility is not an add‑on — it begins with correct HTML.

---

## Common Semantic Mistakes

**Mistake: Using `div` for everything**

Fix:

* pause and ask what the element *is*

---

**Mistake: Styling headings instead of using them properly**

Fix:

* use headings for structure
* style them later

---

**Mistake: Using links for actions**

Fix:

* use buttons for actions

---

## Semantics Checklist

Before moving on to Selectors, confirm:

* landmarks are used correctly
* sections group related content
* headings follow a logical order
* buttons and links are used correctly

If anything feels unclear, fix semantics before adding classes or CSS.

---

## What Comes Next

Once semantics are correct:

* decide how CSS and JavaScript will target elements (Selectors)

Semantics is the foundation for everything that follows.

# Doc 03 — Selectors: How CSS and JavaScript Target Elements

## Purpose of This Document

This document explains **Selectors** in the Penstock Page‑Building Model.

Selectors answer one practical question:

> **How do CSS and JavaScript find the right elements?**

Selectors are the bridge between:

* HTML (structure and semantics)
* CSS (styling)
* JavaScript (behavior)

Good selectors make pages:

* easier to style
* easier to maintain
* easier to enhance with JavaScript

Poor selectors lead to brittle CSS and confusing scripts.

---

## Selectors Come After Semantics

Selectors are chosen **after** structure and semantics are correct.

You should already know:

* what elements exist
* what each element means

Selectors do **not** decide:

* layout
* visual design
* behavior logic

Selectors only decide **how elements are targeted**.

---

## What Counts as a Selector

In Penstock, selectors include:

* class names (e.g. `.service-card`)
* data attributes (e.g. `[data-state="open"]`)
* ARIA attributes (e.g. `[aria-expanded="true"]`)

These are the **only intentional ways** CSS and JavaScript should target elements.

---

## The Core Rule: Select by Meaning

Selectors should reflect **what something is**, not where it happens to live in the DOM.

Good:

* `.site-header`
* `.hero`
* `.service-card`

Avoid:

* `.homepage > div > div > ul > li`
* `.left-column`
* `.blue-box`

If a selector would stop making sense after a layout change, it is probably the wrong selector.

---

## Classes as the Primary Selector

Class names are the primary selector type in Penstock.

Why:

* they are explicit
* they are readable
* they are stable over time

Classes should:

* describe the block or element
* avoid encoding layout or color

Class names work hand‑in‑hand with the BEM-style naming rules defined in Doc 00.

---

## Attribute Selectors for State

Use attributes to represent **state**.

Common examples:

* `aria-expanded="true" / "false"`
* `data-state="open" / "closed"`

CSS and JavaScript can both react to these states.

Rules:

* attributes describe *condition*, not style
* JavaScript updates state
* CSS responds visually

This keeps behavior simple and predictable.

---

## Avoiding DOM-Dependent Selectors

Avoid selectors that depend on:

* element depth
* sibling order
* exact nesting structure

Examples to avoid:

* `header nav ul li a`
* `.card > div > p`

These selectors break easily when structure changes.

Prefer a clear class or attribute instead.

---

## Selectors and JavaScript (Beginner-Safe)

JavaScript should:

* look for clear selectors
* change attributes or classes
* avoid walking the DOM blindly

You should be able to explain JavaScript behavior like this:

> “When this button is clicked, change this state.”

If the script needs complex logic just to *find* elements, selectors are likely the problem.

---

## When to Add a Selector (and When Not To)

Add a selector when:

* CSS needs to style something
* JavaScript needs to interact with something
* state needs to be represented

Do **not** add a selector when:

* the element has no styling or behavior responsibility
* the wrapper exists only for grouping

Fewer selectors = clearer markup.

---

## Common Selector Mistakes

**Mistake: Adding classes "just in case"**

Fix:

* add selectors only when they have a job

---

**Mistake: Styling by accident**

Fix:

* never rely on element position alone

---

**Mistake: Mixing meaning and appearance in names**

Fix:

* name by role, not look

---

## Selectors Checklist

Before moving on to Styling, confirm:

* selectors reflect meaning
* selectors are simple and readable
* state is represented with attributes
* no selectors depend on fragile DOM structure

Selectors should feel boring — that’s a good sign.

---

## What Comes Next

Once selectors are in place:

* apply visual styles using tokens and layout rules (Styling)

Selectors are the last step before CSS becomes productive.

# Doc 04 — Styling: How Visual Design Is Applied Safely

## Purpose of This Document

This document explains **Styling** in the Penstock Page‑Building Model.

Styling answers one focused question:

> **How should this page look and respond visually?**

Styling is about **appearance and layout**, not meaning or behavior.

When styling is applied at the right time and in the right way:

* pages are easier to maintain
* layout changes are safer
* visual updates do not break structure or semantics

---

## Relationship to the Penstock Styling Framework

This document explains **when and why styling decisions are made**.

The *how* of styling — including:

* the Penstock CSS framework
* design tokens
* utilities and primitives
* layout recipes and patterns

is documented separately in the **Penstock Framework**.

Think of the relationship like this:

* **This document** explains *styling responsibility and timing*
* **The Penstock Framework docs** explain *styling implementation details*

If you are unsure *where* a styling decision belongs, stay here.
If you are unsure *how* to implement a styling decision, move to the Penstock Framework.

This separation keeps page-building docs focused and prevents duplication.

---

## Styling Comes After Structure, Semantics, and Selectors

Styling is applied **after**:

* Structure is clear
* Semantics are correct
* Selectors are deliberate

You should already know:

* what elements exist
* what each element means
* how CSS will target them

Styling does **not** decide:

* page content
* HTML elements
* interaction logic

Those decisions are already locked.

---

## What Styling Is Responsible For

Styling controls:

* spacing
* typography
* color
* layout behavior
* visual hierarchy

Styling should:

* respond to structure
* respect semantics
* react to selector state

Styling should **never**:

* fix poor structure
* hide semantic mistakes
* replace missing content decisions

---

## Token‑First Styling

Penstock uses a **token‑first approach** to styling.

Tokens represent:

* spacing values
* font sizes
* colors
* radii
* shadows

Rules:

* tokens are defined globally
* components and pages consume tokens
* raw values are avoided when possible

This keeps visual decisions consistent across the site.

---

## Layout Is Not Structure

Layout is part of styling, not structure.

Examples of layout decisions:

* columns
* grids
* alignment
* responsive behavior

Rules:

* layout responds to existing structure
* layout should not introduce new meaning
* layout should not require extra wrappers unless necessary

If layout feels hard, revisit structure or selectors first.

---

## Styling Sections and Containers

Because Penstock uses a **section + container** pattern:

* sections typically control vertical spacing
* containers control width and inner alignment

Styling should reinforce this pattern, not fight it.

Avoid:

* setting width logic directly on sections
* mixing spacing responsibilities

---

## Styling Reusable Blocks

Reusable blocks (cards, headers, components) should:

* style against their block selector
* avoid relying on page context
* be predictable wherever they appear

Modifiers should adjust appearance, not meaning.

---

## Styling and State

Visual changes based on state should:

* be driven by selectors
* respond to attributes or classes

Examples:

* open / closed
* active / inactive
* featured / default

JavaScript updates state.
CSS reacts visually.

---

## Responsive Styling (High Level)

Responsive behavior is part of styling.

Rules:

* content should remain readable at all sizes
* layout should adapt, not break
* responsiveness should not require new HTML

If responsiveness requires structural changes, revisit structure.

---

## Common Styling Mistakes

**Mistake: Using CSS to fix structure problems**

Fix:

* adjust structure first

---

**Mistake: Hard‑coding values everywhere**

Fix:

* use tokens

---

**Mistake: Over‑styling early**

Fix:

* get structure and semantics right first

---

## Styling Checklist

Before moving on to Scripting, confirm:

* styling responds to structure and selectors
* tokens are used consistently
* layout decisions are isolated to CSS
* visual changes do not affect meaning

Styling should feel controlled and predictable.

---

## What Comes Next

Once styling is stable:

* add behavior where needed (Scripting)

Styling is the final visual layer before interaction.

# Doc 05 — Scripting: Adding Behavior Without Breaking Pages

## Purpose of This Document

This document explains **Scripting** in the Penstock Page‑Building Model.

Scripting answers one careful question:

> **How do we add behavior without breaking structure, semantics, or styling?**

JavaScript is powerful, but in page building it should be:

* intentional
* minimal
* predictable

This document focuses on **responsibility and timing**, not advanced JavaScript techniques.

---

## Relationship to the Penstock JavaScript Framework (If/When It Exists)

This document explains:

* *when* scripting is appropriate
* *what* scripting is responsible for
* *what scripting must not do*

If Penstock later defines:

* shared JavaScript utilities
* common interaction patterns
* helper functions

those details live in a **separate Penstock framework document**.

Think of the relationship like this:

* **This document** = scripting rules and boundaries
* **Framework docs** = scripting implementation details

---

## Scripting Comes After Everything Else

Scripting is added **after**:

* Structure is correct
* Semantics are correct
* Selectors are deliberate
* Styling is stable

You should already know:

* what elements exist
* what each element means
* which selectors represent state

If any of those feel unclear, fix them before writing JavaScript.

---

## What Scripting Is Responsible For

Scripting is responsible for:

* responding to user actions
* changing simple state (open / closed, on / off)
* updating attributes or classes

Scripting is **not** responsible for:

* deciding page structure
* choosing HTML elements
* controlling layout or appearance

JavaScript supports the page — it does not lead it.

---

## Think in Terms of State

Most page interactions can be described as **state changes**.

Examples:

* menu open / menu closed
* accordion expanded / collapsed
* modal visible / hidden

Good scripting follows this pattern:

1. user performs an action
2. state changes
3. CSS responds visually

JavaScript changes state.
CSS handles appearance.

---

## Use Attributes for State

State should usually be represented with:

* ARIA attributes (when appropriate)
* data attributes

Examples:

* `aria-expanded="true"`
* `data-state="open"`

Benefits:

* state is readable in the HTML
* CSS can respond without extra classes
* accessibility improves automatically

---

## Keep JavaScript Small and Isolated

Rules:

* write small scripts for specific behaviors
* avoid global logic when possible
* keep scripts close to the feature they support

If a script grows large, that is a signal to:

* revisit structure
* revisit selectors
* simplify behavior

---

## Progressive Enhancement

Pages should still:

* load
* read
* make sense

without JavaScript.

Scripting should enhance the experience, not replace core content.

If content disappears without JavaScript, reconsider the approach.

---

## Common Scripting Mistakes

**Mistake: Using JavaScript to fix HTML problems**

Fix:

* correct semantics or structure first

---

**Mistake: Letting JavaScript control layout**

Fix:

* move layout logic back to CSS

---

**Mistake: Over‑engineering interactions**

Fix:

* reduce behavior to simple state changes

---

## Scripting Checklist

Before considering scripting complete, confirm:

* behavior is necessary
* structure and semantics are unchanged
* state is visible in the markup
* CSS handles visual changes
* JavaScript is readable months later

If scripting feels complicated, something earlier is likely off.

---

## Final Note

Good page building does not avoid JavaScript.

It **respects its role**.

When scripting is added last and kept small, pages stay flexible, accessible, and easy to maintain.

This completes the Penstock Page‑Building document set.
