# Health Quarters

![CI](https://github.com/your-org/health-quarters/actions/workflows/ci.yml/badge.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Node](https://img.shields.io/badge/node-22.x-green.svg)

A clinical and public health intelligence platform. It separates two distinct roles — a **Public Health Admin** who works with anonymised aggregate data, and a **Clinician** who accesses individual patient records through QR-verified sessions — and makes that separation visible and auditable in the UI.

**Live demo:** [health-quarters.vercel.app](https://health-quarters.vercel.app)

---

## What it does

**Public Health Admin workspace**
- Dashboard with KPI cards and trend charts across disease categories
- Disease Intelligence table with signal scoring and case counts
- Forecasting with confidence intervals across three time windows
- Anomaly detection queue with severity triage
- Privacy Center — demonstrates K-anonymity enforcement (queries that would return fewer than 10 people are automatically suppressed)
- Audit Logs — every access and query is logged, but patient identifiers are never exposed to the admin role

**Clinician workspace**
- QR Patient Scanner with countdown session timer
- Patient Record for Rahul Sharma (PAT-1042) with medical history timeline, diagnosis highlight, and prescriptions
- Access History (shared audit view filtered to clinical events)

**Access control demo**
- If a Public Health Admin tries to open a patient record, they hit an explicit "Access Denied" screen
- The denial is logged to the audit trail automatically
- A "Switch to Clinician Workspace" button lets the demo flow continue without dead ends

---

## Tech stack

| Layer | Choice |
|---|---|
| Framework | React 19 |
| Build | Vite 8 (Rolldown) |
| Styling | Tailwind CSS v4 |
| Icons | Lucide React |
| Language | TypeScript 5.7 |
| Deploy | Vercel |
| Package manager | pnpm 10 |

No backend. All data is synthetic and hard-coded for the demo. Nothing in this app stores or transmits real patient data.

---

## Running locally

```bash
# clone and install
git clone <repo-url>
cd health-quarters
pnpm install

# start dev server
pnpm dev
```

The dev server starts on `http://localhost:5173`.

```bash
# production build
pnpm build

# preview the build
pnpm preview
```

Node 22.x is required. The project uses `pnpm` as its package manager.

---

## Project structure

```
src/
  App.tsx        — entire application: components, data, shell, pages
  index.css      — design tokens, global styles, component CSS
  main.tsx       — React entry point

docs/
  DESIGN_SYSTEM.md    — colour tokens, typography, component conventions
  ARCHITECTURE.md     — how the workspace / RBAC model works
  PRIVACY_MODEL.md    — K-anonymity enforcement and audit log design

scripts/
  setup-figma.mjs     — creates .figma/make/site.json if missing (used in CI)
```

The whole app lives in `src/App.tsx`. It's a single-file architecture chosen deliberately for the hackathon — fast to iterate, easy to review end-to-end, no build-time routing complexity.

---

## Evaluation criteria addressed

| Criteria | How |
|---|---|
| **Innovativeness** | Role-aware UI that makes RBAC visible, not just enforced in code |
| **Problem Understanding** | Two clearly separated workspaces reflecting real public-health vs clinical access patterns |
| **Tech Stack** | React 19 + Vite 8 (Rolldown) + Tailwind v4 — all current-generation tooling |
| **UI/UX** | Collapsible sidebar, QR session timer, Access Denied intercept, clinical timeline |
| **GitHub Maintenance** | Structured docs, conventional commits, Vercel CI/CD |
| **Documentation** | README, design system reference, architecture notes, privacy model |
| **Social Impact** | Patient privacy by design — K-anonymity, audit trail, role-gated access |

---

## Synthetic data notice

All patient data in this demo is fictional. PAT-1042 (Rahul Sharma) does not represent a real person. Disease statistics are invented for demonstration purposes only.

---

## Deployment

The repo is connected to Vercel. Every push to `main` triggers a production deploy.

```json
{
  "installCommand": "pnpm install --no-frozen-lockfile",
  "buildCommand": "node -e \"...create site.json...\" && pnpm exec vite build",
  "outputDirectory": "dist"
}
```

Node version is pinned to `22.x` in both `package.json` engines and `.nvmrc` to ensure native binary compatibility with the Rolldown bundler.

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for setup instructions and pull request guidelines.

## License

MIT — see [LICENSE](./LICENSE).
