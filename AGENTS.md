# AGENTS.md — brandongallagher1999

Agent guide for this GitHub Pages personal site. Prefer small, reviewable changes.

## Project

Static marketing site for Brandon Gallagher (AI Platform Engineer).

| Path | Role |
|------|------|
| `index.html` | Entire site (HTML + CSS + light JS) |
| `README.md` | GitHub profile README (skills badges) |
| `assets/brandon.jpg` | Hero portrait |
| `assets/Brandon-Gallagher-Resume.pdf` | Downloadable resume |
| `assets/logos/` | Client logos for the carousel |

Hosted via GitHub Pages from the repo root (`index.html`).

## Non-negotiables

- Keep the hero as one composition: brand name first, one headline, one lede, one CTA group, full-bleed portrait.
- Preserve the charcoal / leather / cream palette (`--charcoal`, `--leather`, `--cream`).
- Do not introduce a bundler, framework, or package manager unless explicitly requested.
- Prefer Bun for any one-off tooling scripts (`bun`, `bunx`); never npm/yarn/pnpm unless asked.
- Never commit secrets, credentials, or private contact details beyond what already lives on the public page.

## Atomic change practices

Ship **one concern per commit**. If a change spans unrelated goals, split it.

### Good atoms

| Atom | Examples |
|------|----------|
| Copy / positioning | Hero headline, focus bullets, meta description |
| Layout / CSS | Hero crop, spacing, typography, motion |
| Assets only | Swap a logo, update resume PDF, replace portrait |
| Carousel / clients | Logo list, marquee behavior, card chrome |
| Profile links / CTAs | GitHub, LinkedIn, email, Calendly, resume download |
| Profile README | Badge list / technology inventory in `README.md` |
| Docs / agent guidance | `AGENTS.md`, comments that explain non-obvious constraints |

### Bad mixes (do not batch)

- Site redesign + README badge rewrite + logo swaps in one commit
- Copy rewrite buried inside a CSS-only spacing tweak
- Generated/tooling noise mixed with product UI

### Commit message style

- Prefer conventional, imperative subjects: `feat:`, `fix:`, `style:`, `docs:`, `assets:`
- One short subject line; optional body for *why*
- Match existing history tone when reasonable; still prefer clarity over vague titles like `update` or `initial page`

Examples:

```text
feat: add dark client logo carousel
fix: keep hero face in frame on wide viewports
assets: replace Deloitte logo for dark theme contrast
docs: align README badges with resume skills
```

### Working loop for agents

1. State the single outcome for this commit.
2. Touch only the files needed for that outcome.
3. Self-check: “Could this be two PRs/commits without losing meaning?” If yes, split.
4. Stage explicitly (`git add <paths>`), never blanket `git add .` when unrelated dirt exists.
5. Commit with a subject that names the *why* or the user-visible change.
6. Do not amend or force-push unless the user explicitly asks.

## Design constraints (site)

- Full-bleed hero portrait; pin `object-position` so the face stays visible on wide aspect ratios.
- Logo files should be trimmed with transparent (or brand) backgrounds so cards do not show black boxes.
- Client logos scale inside a shared `.client-card__mark` frame with `object-fit: contain`.
- Prefer SVG sprite icons for CTAs/profile links; keep icons sized with the link text.
- Respect `prefers-reduced-motion` for kenburns / marquee.

## Resume / messaging source of truth

When updating positioning or README tech lists, prefer the current resume PDF and live bio:

- Role: AI Platform Engineer; Azure / Terraform / Kubernetes
- Emphasis: enterprise-scale, compliant **Agentic Control Planes**
- Financial clients/institutions shown: Scotiabank, CIBC, Haventree Bank, Interac, RBC, Deloitte

## Verification

- Open `index.html` locally (or a simple static server) after hero/CSS/logo changes.
- Spot-check desktop wide aspect ratios and mobile for face crop + logo readability.
- Confirm resume download path: `assets/Brandon-Gallagher-Resume.pdf`.
