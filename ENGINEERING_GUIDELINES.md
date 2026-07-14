# Engineering Guidelines

Engineering standards for `demo-repository` — a small static web sample
(`index.html`, `package.json` depending on `@primer/css`). The bar is
intentionally lightweight, but the same discipline applies.

## Principles

1. **Understand before changing.** Read `index.html` and `package.json` before
   editing; keep changes scoped to what the task needs.
2. **Smallest safe change.** No speculative rewrites, no unrelated reformatting.
3. **Keep it working.** `index.html` must render as valid, standalone HTML.

## Code style

- Semantic, accessible HTML; keep markup valid and links resolving.
- Prefer the `@primer/css` design system already declared in `package.json` over
  ad-hoc inline styles.
- Pin dependency versions in `package.json` (as `@primer/css` already is). Do not
  add dependencies the demo does not use.

## Security

- Never commit secrets, tokens, or credentials.
- Do not add third-party `<script>` tags or external network calls without a clear
  reason — a demo page should stay self-contained and safe to open.
- Sanitize any user-supplied content before inserting it into the DOM.

## Commits & pull requests

- Branch from `main`; lowercase, hyphen-separated, scoped branch names.
- One logical change per PR, with a clear title and description.
- Open as a draft until any CI checks are green.
