# AGENTS.md — Penstock Design & Marketing (Astro)

This file defines **how AI agents (Codex)** are allowed to work inside this repository.
It is intentionally short. All deep rules live in `/docs` and must be followed exactly.

---

## 1. Project Summary

This repository contains the Penstock Design & Marketing website.

Framework:

* Astro (static-first)
* Markdown + front matter for content

Positioning:

* Consultant-led marketing + design
* Plain-spoken, Newfoundland-first language
* Strategy-first, execution-capable

Current Phase:

* Build **site architecture and page shells only**
* No final copy, no CMS, no advanced styling

---

## 2. Source of Truth (READ FIRST)

Before making any changes, agents MUST read:

1. `/docs/00_SITE_PLAN.md`
2. `/docs/01_PAGE_BUILDING.md`
3. `/docs/02_PENSTOCK_FRAMEWORK.md`
4. `/docs/03_BLOG_SYSTEM.md` (when blog work is requested)
5. `/docs/component-thinking.md`

If there is a conflict between code and docs, **the docs win**.
If something is unclear, STOP and ask.

---

## 3. Hard Rules / Non‑Goals

Agents MUST NOT:

* Invent new pages, services, or routes
* Rename or restructure URLs
* Introduce a CMS, database, API, or headless system
* Add animations or heavy JS frameworks
* Refactor broadly without explicit instruction
* Change framework or token rules unless asked

---

## 4. Blog Rules (Important)

A blog WILL exist, but:

* Blog content = markdown files with front matter
* Static generation only
* No database, no admin UI, no authentication
* No headless CMS or API integrations

Follow `/docs/03_BLOG_SYSTEM.md` exactly.

---

## 5. Page Structure Enforcement

All pages MUST follow the standard section order defined in:

* `/docs/01_PAGE_BUILDING.md`

Do not invent new section orders.
Use placeholder headings and notes only.

---

## 6. Change Discipline

* Make small, reviewable changes
* Explain what was created or modified
* Ask before doing structural refactors

---

## 7. Definition of Done

A task is complete when:

* The page exists at the correct URL
* Navigation links correctly
* The standard page structure is used
* No extra features or pages were introduced
* No rules above were violated
