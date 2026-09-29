# Contributing

Thanks for taking the time to look at this project.

## Getting started

```bash
git clone <repo-url>
cd health-quarters
pnpm install
pnpm dev
```

The dev server starts at `http://localhost:5173`. Changes to `src/` hot-reload immediately.

## Project layout

Almost everything lives in two files:

- `src/App.tsx` — all components, data, and page logic
- `src/index.css` — design tokens and styles

If you're making a UI change, you'll almost certainly be editing one or both of these. The docs in `docs/` explain the design system and architecture in more detail.

## Making changes

1. Fork the repo and create a branch: `git checkout -b your-feature`
2. Make your changes
3. Run `pnpm build` to check it compiles cleanly
4. Commit with a short, descriptive message
5. Open a pull request

## Commit style

We use conventional commit prefixes loosely:

```
feat: add something new
fix: correct a bug
docs: update documentation
style: visual or formatting change with no logic change
refactor: restructure without changing behaviour
```

## Synthetic data

All patient data in the demo is fictional. If you add new demo data, keep it clearly fictional — no real names, real addresses, or real clinical records.

## Questions

Open an issue and we'll respond when we can.
