# 90817.com · HB Power Tower Co., Ltd.

> Transmission tower manufacturer serving Southeast Asia, Middle East, Africa, and Latin America.

## What is this repo

This is the source code for [90817.com](https://90817.com) — the B2B branding + inquiry site for **HB Power Tower Co., Ltd.**, a steel structure tower manufacturer specializing in:

- **Transmission line towers** (66 kV – 1000 kV AC / ±800 kV DC, all structure types)
- Substation structures
- Communication towers
- Other steel structure towers (wind, observation, training)

## Tech stack

- **Astro** (static site generator, MDX content)
- **Tailwind CSS** (utility-first styling)
- **Cloudflare Pages** (global CDN, free tier)
- **English only** (single language, no i18n)

## Project governance

This repo is forked from the [kiro.dev Harness Engineering starter kit](https://github.com/liupengceo/kiro.dev) and follows its full process:

- Read [`AGENTS.md`](./AGENTS.md) before doing anything
- Every task needs an ExecPlan (see `templates/ExecPlan.md`)
- Every PR uses the template in `.github/pull_request_template.md`
- Harness changes go through independent PRs with `harness-change` label

## Key decisions

- **ADR-0001**: Tech stack + starter kit adoption (see `docs/adr/`)
- **Primary product**: Transmission towers (all voltages, all structure types)
- **Target markets**: Southeast Asia, Middle East, Africa, Latin America
- **Brand name**: HB Power Tower Co., Ltd.
- **Contact**: sales@90817.com (Cloudflare Email Routing → owner's inbox)
- **Path**: A only (brand + inquiry site; no SEO content farm)

## Local development

```bash
# Prerequisites: Node.js 20+, pnpm
pnpm install
pnpm dev          # http://localhost:4321

# Pre-commit (inherited from kiro.dev)
pip install pre-commit pyyaml
pre-commit install
pre-commit install --hook-type commit-msg
```

## Directory structure

```
.
├── AGENTS.md                    # Agent contract (from kiro.dev)
├── .kiro/steering/              # Steering rules
├── src/                         # Astro source (pages, components, content)
│   ├── pages/
│   ├── components/
│   ├── content/                 # MDX product/project/capability pages
│   └── layouts/
├── public/                      # Static assets (images, PDFs, logo)
├── docs/
│   ├── adr/                     # Architecture decisions
│   └── harness-engineering/     # Knowledge base (from kiro.dev)
├── plan/                        # Long-task memory
│   ├── execplans/
│   ├── sessions/
│   └── decisions/
├── templates/                   # ExecPlan + review personas
└── .github/                     # PR/issue templates + workflows
```

## License

[Apache License 2.0](./LICENSE)

---

**For agents**: start with [`AGENTS.md`](./AGENTS.md), then read the current ExecPlan in `plan/execplans/`.
