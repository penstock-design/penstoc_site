# Penstock Component Thinking

## A Spoken Walkthrough Using a Card Component Example

---

### Purpose of this document

This document explains **how we think about components** in the Penstock framework.

It is intentionally written in a *spoken*, human style.

It is **not** meant to be clever, dense, or optimized for speed.
It is meant to slow you down, reinforce correct mental models, and act as a grounding reference when things start to feel fuzzy.

This document is designed to be **read alongside `AGENTS.md`**.

* `AGENTS.md` defines the rules.
* This document explains *why* those rules exist.

---

## Start with structure — always

Before styles.
Before props.
Before data.
Before loops.

We start with **structure**.

On the page, we have a **section**.

Inside that section, there is an **introduction block**.

That introduction contains:

* A heading
* A short piece of supporting text

This intro is a **pattern**.

It is not specific to one page.
It can be reused anywhere.

After the intro, we have a **list of cards**.

---

## The card list is semantic

The list is an **unordered list**.

Each card lives inside a **list item**.

Inside each list item, the card itself is rendered.

The card is an **`article`**.

Not a div pretending to be content.
An actual article element.

This choice matters for:

* Semantics
* Accessibility
* Long‑term clarity

---

## Internal structure of a card

Inside the article, the structure is deliberate.

### Optional media

Optionally, there may be a **figure**.

The figure contains an image.

If there is **no image**, the figure does **not exist at all**.

We do **not**:

* Hide it
* Leave an empty wrapper
* Rely on CSS to “turn it off”

If it does not belong, it is **not rendered**.

---

### Card content

After the figure, there is a **content wrapper**.

Inside the content wrapper:

* A heading (typically an H3)
* A paragraph for description
* Optionally, a link or button

If the link does not exist, it is **not rendered**.

No empty elements.
No placeholders.

The DOM stays clean.

---

## Props are divided into three categories

This is a **core Penstock rule**.

Props are **never** a flat, unstructured list.

They fall into three intentional groups.

---

### 1. Content props

Content props control **what the card says**.

Examples:

* Title
* Description
* Image
* Href
* Call‑to‑action label

These props vary per instance.

Each card can have different content.

---

### 2. Functionality props

Functionality props control **what the card does**.

Examples:

* `hasImage`
* `hasLink`

These props:

* Do **not** control styling
* Control **structure and rendering**

If `hasImage` is false → the figure does not exist.
If `hasLink` is false → the link does not exist.

This prevents:

* Empty wrappers
* Broken layouts
* Accessibility issues

---

### 3. Style props

Style props control **how the card looks**.

We standardize this as a **single variant prop**.

Example:

```
variant = "default" | "dark" | "outline"
```

We do **not** stack multiple style booleans.

One prop.
A known set of values.
Predictable output.

---

## Variants are controlled using data attributes

This is a **locked Penstock pattern**.

The root `article` element receives a data attribute:

```
data-variant="default"
data-variant="dark"
data-variant="outline"
```

Values are always **lowercase**.

We use data attributes because they are:

* Explicit
* Inspectable
* Non‑colliding
* Declarative

All variant styling stays **scoped to the component**.

No global variant classes.

---

## Conditions remove elements — they do not hide them

This is a rule, not a preference.

If something is optional, it is **conditionally rendered**.

We do **not** render and hide.

This keeps:

* Accessibility correct
* Markup readable
* Layout predictable
* Future debugging sane

---

## Looping is just data mapping

Components do **not** care where data comes from.

In Penstock, looping data can come from:

* Astro content collections
* Static JSON files
* Page‑level props

The component:

* Receives data
* Does not fetch data
* Does not know about loops

A component should behave the same way whether it is used once or a hundred times.

---

## Responsiveness happens at the block level

We do **not** design around global breakpoints.

The **grid** decides:

* One column
* Two columns
* Three columns

The **card remains structurally stable**.

The card does not react directly to viewport size.

Breakpoints exist where the layout needs them — not globally.

---

## Final principle

One component should support **many behaviors**.

We do **not** duplicate components to create variations.

We extend components carefully:

* With props
* With conditions
* With variants

This keeps the system:

* Small
* Readable
* Maintainable

---

*End of document.*
