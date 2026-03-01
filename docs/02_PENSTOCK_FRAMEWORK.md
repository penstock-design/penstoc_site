# Penstock CSS Framework — Canonical Spec (ACSS-aligned)

This document is the **authoritative, copy‑paste‑ready specification** for the Penstock CSS framework.

It represents the **most up‑to‑date state** of the framework after auditing against:

* Automatic CSS (ACSS)
* Etch documentation
* Modern CSS practices (ACSS 4.x direction)

This is a **living framework** designed to evolve safely during real production work.

---

## Scope & Constraints

**We do:**

* Borrow directly from ACSS + Etch
* Use modern CSS where it simplifies the system
* Keep the framework intentionally small

**We do NOT:**

* Invent new token systems
* Build a full design system
* Ship large utility libraries
* Pre‑optimize for edge cases

---

## Naming Rules (ACSS)

### t‑shirt sizing

When a token is part of a size family, it uses **t‑shirt sizing**:

* `2xs` `xs` `s` `m` `l` `xl` `2xl`

This applies only to **raw scale tokens**, not contextual assignments.

---

## Core Tokens (Custom Properties)

All tokens are **global** and defined on `:root`.

### 1) Spacing Scale (Raw)

```css
--space-2xs
--space-xs
--space-s
--space-m
--space-l
--space-xl
--space-2xl
```

---

### 2) Section Spacing (Contextual)

```css
--section-space-2xs
--section-space-xs
--section-space-s
--section-space-m
--section-space-l
--section-space-xl
--section-space-2xl
```

Rule:

* Sections use `section-space`
* Components use `space`

---

### 3) Contextual Spacing (ACSS)

```css
--container-gap
--content-gap
--grid-gap
```

These map to the spacing scale internally.

---

### 4) Width & Layout

```css
--content-width
--gutter
```

No secondary width abstractions.

---

### 5) Typography

#### Font Families

```css
--heading-font-family
--body-font-family
```

#### Heading Sizes

```css
--h1
--h2
--h3
--h4
--h5
--h6
```

#### Text Sizes (t‑shirt)

```css
--text-2xl
--text-xl
--text-l
--text-m
--text-s
--text-xs
```

#### Shared Heading Defaults

```css
--heading-line-height
--heading-font-weight
--heading-letter-spacing
```

---

### 6) Color Tokens (ACSS 4.x Direction)

#### Core Palette Roles

```css
--primary
--secondary
--tertiary
--accent
--base
--neutral
```

#### Shade Pattern (per role)

```css
--{color}-ultra-light
--{color}-light
--{color}-semi-light
--{color}-semi-dark
--{color}-dark
--{color}-ultra-dark
--{color}-hover
```

Example:

* `--primary-dark`
* `--neutral-ultra-light`

#### Contextual Color Assignments

```css
--body-bg-color
--bg-ultra-light
--bg-light
--bg-dark
--bg-ultra-dark

--body-color
--text-dark
--text-dark-muted
--text-light
--text-light-muted
```

---

### 7) Border & Radius

```css
--radius

--border
--border-light
--border-dark
```

---

## Modern Color System Rules (ACSS 4.x)

* Prefer OKLCH‑friendly values
* Enable UA‑aware theming
* Use `light-dark()` for dual‑mode values
* Do NOT create transparency token libraries
* Use `color-mix()` and Relative Color Syntax for alpha

### Dark Mode Baseline

```css
:root {
  color-scheme: light dark;
}
```

Example assignment:

```css
:root {
  --body-bg-color: light-dark(var(--bg-ultra-light), var(--bg-ultra-dark));
  --body-color: light-dark(var(--text-dark), var(--text-light));
}
```

---

## Structural Elements (Etch‑Style)

These exist to give **page‑builder speed** with real HTML.

### Section

```html
<section class="section">
  <div class="container">…</div>
</section>
```

### Container

```html
<div class="container">…</div>
```

### Flex Div

```html
<div class="flex">…</div>
```

### Div (unstyled)

```html
<div>…</div>
```

### Anchor

```html
<a class="link" href="#">…</a>
```

---

## Token Stability & Refactors (Production Rule)

* Token **values** may change anytime
* Token **names are API** and must not be casually changed

### Controlled Rename Workflow

1. Add the new token
2. Alias the old token to the new one
3. Update all usages
4. Verify zero remaining references
5. Remove alias only when explicitly approved

Example:

```css
:root {
  --new-token: ...;
  --old-token: var(--new-token);
}
```

---

## Framework Evolution Philosophy

* This framework is allowed to change
* Changes must be deliberate and documented
* Real pages come first; abstractions follow

> Build → feel friction → adjust framework → repeat

---

**Status:** Canonical / Production‑Ready
**Framework:** Penstock CSS
**Alignment:** ACSS + Etch + Modern CSS
