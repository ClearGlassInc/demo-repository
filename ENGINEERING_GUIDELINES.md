# Engineering Guidelines

Engineering standards for `demo-repository` — the organization's GitHub demo
repo: a single static page (`index.html`), a `package.json` carrying the
`@primer/css` stylesheet dependency, and two GitHub Actions workflows.
Minimal by design, but the same discipline applies.

## Principles

1. **Understand before changing.** Read the page, `package.json`, and the
   workflows before editing; keep changes scoped to the task.
2. **Smallest safe change.** This repo exists to demonstrate GitHub features
   with the least amount of noise — keep it that way. No speculative
   additions or unrelated rewrites.
3. **Keep CI green.** The **Proof HTML** workflow validates all HTML on every
   push; a change is not done until it passes.

## HTML & content

- `index.html` must remain valid HTML — `proof-html` checks markup and links
  on every push, so broken tags or dead links fail CI.
- Prefer semantic elements and accessible markup (meaningful headings, `alt`
  text on any images you add).
- Keep the page self-contained; if you add assets, reference them with
  relative paths so the page renders the same everywhere.

## Dependencies

- `package.json` intentionally carries a single dependency (`@primer/css`).
  Pin exact versions, and don't add dependencies unless the demo genuinely
  needs them.

## Workflows & security

- Workflows (`.github/workflows/`) must declare explicit least-privilege
  `permissions:` blocks, as `proof-html.yml` (`contents: read`) and the
  job-level grants in `auto-assign.yml` already do.
- Never commit secrets, API keys, or tokens — use GitHub Actions secrets
  (workflows already use `secrets.GITHUB_TOKEN`).
- Pin third-party actions to a specific version, never a floating branch.

## Commits & pull requests

- Branch from `main`; lowercase, hyphen-separated, scoped branch names.
- One logical change per PR with a clear title and description.
- Open as a draft until the Proof HTML check is green.
