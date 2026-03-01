# SOP: Penstock Astro Project Workflow

## 1. Purpose
This SOP defines the standard workflow for building marketing websites with Astro + Penstock.

Goals:
- Start each project consistently.
- Keep code readable and token-driven.
- Translate strategy/content/inspiration into production code with minimal friction.
- Deploy reliably with a default path and a fallback path.

---

## 2. Scope
Default project type: marketing websites.

Out of scope by default:
- Complex product dashboards/web apps (unless explicitly requested).

---

## 3. Operating Model
- User is architecture lead and decision maker.
- Codex implements structure, code, and workflow enforcement.
- `AGENTS.md` in each project is the startup trigger.
- This SOP is the source of process truth.
- This SOP is the workflow layer; Penstock docs remain the deep reference layer.

Primary SOP path:
`/Volumes/2TB_SSD/01 Projects/2026-PDM-PenstockFramework/SOP_PENSTOCK_PROJECT_WORKFLOW.md`

Penstock reference docs (load as needed during build):
- `/Volumes/2TB_SSD/01 Projects/2026-PDM-PenstockFramework/docs/01_PAGE_BUILDING.md`
- `/Volumes/2TB_SSD/01 Projects/2026-PDM-PenstockFramework/docs/02_PENSTOCK_FRAMEWORK.md`
- `/Volumes/2TB_SSD/01 Projects/2026-PDM-PenstockFramework/docs/component-thinking.md`

Skill orchestration during build:
- Use `frontend-design` for page/interface design quality and production-ready visual execution.
- Use `figma` or `figma-implement-design` when Figma links/nodes are provided.
- Use Penstock docs above to enforce framework and build-order rules.

---

## 4. Source-of-Truth Priority
1. User direction (explicit overrides).
2. Figma files (when provided).
3. Inspiration screenshots (directional).
4. Existing framework defaults.

If screenshots conflict and no notes exist:
- Synthesize common patterns.
- Ignore outliers.

---

## 5. Standard Project Lifecycle
1. Create a new project directory.
2. Open project in Codex / IDE.
3. Ensure `AGENTS.md` exists and is read first.
4. Create or verify planning/content/inspiration folders.
5. Initialize Astro project.
6. Apply Penstock framework into Astro project.
7. Add strategy/content markdown and visual context.
8. Translate design direction into project tokens.
9. Build sections/components iteratively.
10. Run QA gates.
11. Deploy (Hetzner VPS default).
12. Hand off final notes.

---

## 6. Required Project Structure
Use a configurable Astro app folder name:
- Default: `build`
- Allowed alternatives: `site` or `dev`
- In this SOP, this folder is referenced as `<app-dir>`.

### 6.1 Required at project start (before Astro init)

```text
<project-root>/
  AGENTS.md
  planning/
  content/
  context/
    inspiration/
  framework/
    styles/
      tokens.css
      base.css
      global-defaults.css
      index.css
```

### 6.2 Required after Astro init completes

```text
<project-root>/<app-dir>/
  src/
    styles/
      tokens.css
      base.css
      global-defaults.css
      index.css
```

Notes:
- `context/inspiration/` accepts images with no strict naming requirement.
- Optional notes file: `context/inspiration/INSPIRATION.md`.
- `framework/styles/` is the source location for Penstock CSS files before Astro exists.

---

## 7. Planning and Content Contracts
Minimum docs to create (if missing):
- `planning/strategy.md`
- `planning/sitemap.md`
- `planning/page-briefs.md`
- `content/home.md` (+ one markdown file per page)

### 7.1 strategy.md minimum fields
- Audience
- Offer / value proposition
- Primary CTA
- Trust blockers
- Constraints

### 7.2 sitemap.md minimum fields
- Page list
- Navigation hierarchy
- Priority pages

### 7.3 page-briefs.md minimum fields (per page)
- Page goal
- Required sections
- Primary and secondary CTAs
- Supporting proof/content requirements

Codex behavior:
- If files are missing, create them.
- If content is missing, request user input and write it into files.

---

## 8. Visual Inspiration Contract
Accepted inputs:
- Any analyzable image format (`.png`, `.jpg`, `.jpeg`, `.webp`, `.gif`, `.svg`, etc.).
- Optional `INSPIRATION.md` notes.
- Optional Figma links.

Rules:
- No strict file naming required.
- Images alone are valid.
- Notes are optional and only increase precision.

---

## 9. Typography and Font Integration
Default approach:
- Google Fonts CDN preferred for speed and simplicity.

Allowed alternatives:
- Local font files provided by user.
- Both CDN + local.

Precedence:
- If both are provided, local files are authoritative.

Implementation rules:
- Wire font setup in Astro project files.
- Map font families into Penstock token layer.
- Avoid hardcoding font families across components.

---

## 10. Tokenization Contract (Project-Specific)
Each project has its own visual tokens.

Rules:
- Project palettes do not need to match other projects.
- Map selected design colors to Penstock token names.
- Use tokens in components; avoid ad hoc raw values.
- If token gaps exist, create RFC entry before implementation.

---

## 11. Penstock Build Order (Mandatory)
Always build in this order:
1. Strategy
2. Systems
3. Structure
4. Semantics
5. Selectors
6. Styling
7. Scripting

Stop conditions:
- If structure is unclear, pause before semantics.
- If semantics are unclear, pause before selectors.
- If tokens are missing, pause and resolve via RFC.
- Do not use CSS/JS to solve strategy/structure problems.

---

## 12. Component Rules
- Structure-first, semantic HTML.
- Optional elements are conditionally rendered, not hidden placeholders.
- Variants use `data-variant` on component roots.
- Naming follows Penstock BEM-style conventions.
- Components receive data; they do not fetch data directly.

---

## 13. Astro Initialization + Penstock Apply
### 13.1 Astro init (inside project)
```bash
npm create astro@latest build
cd build
npm install
npm run dev
```

If you choose a different folder name, replace `build` with `site` or `dev`.

### 13.2 Penstock apply step (standardized action)
After Astro init, apply Penstock into the Astro project by:
1. Copying framework styles from `<project-root>/framework/styles/` into `<app-dir>/src/styles/`.
2. Wiring style imports and global entry points.
3. Ensuring base layout or app entry references `src/styles/index.css`.
4. Seeding project context files/folders if missing.

Note: this may be manual or scripted; behavior must remain consistent.

### 13.3 CSS transfer checklist (required)
Use this checklist every project:
1. Confirm source files exist in `<project-root>/framework/styles/`:
   - `tokens.css`
   - `base.css`
   - `global-defaults.css`
   - `index.css`
2. Confirm destination exists: `<app-dir>/src/styles/`.
3. Copy (or move) the four files into `<app-dir>/src/styles/`.
4. Verify `index.css` imports resolve correctly.
5. Verify app entry/layout imports `src/styles/index.css`.
6. Start dev server and confirm styles are loaded.

Implementation note:
- If your Apple Shortcuts scaffold creates `framework/styles/` by default, this checklist becomes a simple transfer step after Astro init.

---

## 14. Git and GitHub Workflow
Initialize GitHub early.

Recommended checkpoints:
1. `init-astro-baseline`
2. `apply-penstock-bootstrap`
3. `add-strategy-and-content`
4. `structure-semantics-pass`
5. `component-build-pass`
6. `pre-deploy-stabilization`

Guidelines:
- Commit small, meaningful increments.
- Push continuously for recovery and collaboration.

---

## 15. Build Loop (Collaboration)
While building:
1. User gives architecture and priorities.
2. Codex selects and applies relevant skills for the task:
   - `frontend-design` for implementation quality and design execution.
   - `figma`/`figma-implement-design` for Figma-driven translation.
3. Codex implements code changes.
4. User reviews in local dev server/browser.
5. Iterate until acceptance gates pass.

This loop remains active until the site is complete.

---

## 16. QA and Completion Gates
A project is complete only when all pass:
1. Semantic landmarks and heading hierarchy are valid.
2. Mobile and desktop layouts are verified.
3. Token usage is consistent and readable.
4. No fragile DOM-dependent selector chains.
5. JS is minimal and state-driven.
6. Core pages and CTAs are functioning.
7. Build/deploy pipeline is successful.

---

## 17. Deployment Runbook
### 17.1 Default: Hetzner VPS (Enhance panel)
Use Hetzner VPS with Enhance as the default deployment destination.

Standard flow:
1. Build static Astro output.
2. Provision or select target site/domain in Enhance panel.
3. Configure web root/static serving for the built output.
4. Upload/deploy built files to the configured web root.
5. Verify domain routing, SSL, and cache behavior.
6. Record deployment + rollback notes in project docs.

### 17.2 Optional Alternative: Cloudflare Pages
Use when explicitly chosen for a project.

Standard flow:
1. Connect GitHub repository.
2. Configure build command and output directory for Astro.
3. Enable preview deploys for branches.
4. Promote approved main branch to production.
5. Verify domain + SSL.

---

## 18. Extension RFC Template
Create an RFC entry when framework extension is needed.

Required fields:
- Problem statement
- Proposed token/primitive name
- Proposed value(s) and rationale
- Impacted components/pages
- Backward compatibility/migration notes
- Approval status

---

## 19. Startup Checklist (Per New Project)
When a new project opens, Codex should:
1. Read `AGENTS.md` first.
2. Confirm project is website mode.
3. Check/create folder structure.
4. Check/create planning/content files.
5. Confirm inspiration sources present or request them.
6. Confirm Astro init status.
7. Apply/verify Penstock styles.
8. Begin layer-by-layer build plan.

---

## 20. Post-Launch Handoff
Provide:
1. What was implemented.
2. Final token/font choices.
3. Any approved RFC extensions.
4. Known follow-ups.
5. Deployment location and status.
