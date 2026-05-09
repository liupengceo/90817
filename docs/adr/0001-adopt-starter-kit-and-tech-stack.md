# ADR-0001 · Adopt kiro.dev starter kit + Astro + Tailwind + Cloudflare Pages

- **Status**: Accepted
- **Date**: 2026-05-10
- **Author**: @liupengceo + kiro agent

## Context

We are building a B2B branding + inquiry website for HB Power Tower Co., Ltd. at `90817.com`. The site's purpose is to establish trust with overseas EPC contractors and power grid companies in Southeast Asia, Middle East, Africa, and Latin America, and convert them into inquiry-form submissions.

Key constraints:
- Owner is not a frontend developer; agent does all coding
- Target audience is in regions with slow internet (Africa, rural SEA)
- Content is English-only
- Budget is minimal (prefer free hosting tiers)
- Must be maintainable by an AI coding agent long-term

## Decision

Adopt the following stack:

1. **Governance**: Fork [liupengceo/kiro.dev](https://github.com/liupengceo/kiro.dev) starter kit (AGENTS.md, steering rules, ExecPlan templates, review personas, pre-commit hooks, CI workflows)
2. **Framework**: Astro (static site generator with MDX content)
3. **Styling**: Tailwind CSS (utility-first, agent-friendly)
4. **Hosting**: Cloudflare Pages (free tier, global CDN, edge performance)
5. **Email**: Cloudflare Email Routing (sales@90817.com → owner's Gmail)
6. **Analytics**: Plausible or Umami (privacy-respecting, no cookie banner needed)
7. **Language**: English only (no i18n infrastructure)

## Considered alternatives

| Option | Pros | Why rejected |
|---|---|---|
| WordPress + Elementor | Non-technical editing | Plugin security debt, slow in Africa/SEA, agent-unfriendly |
| Next.js | Most popular React framework | Overkill for static B2B site, adds server complexity |
| Hugo | Fastest build | Go templates hard for agent to maintain reliably |
| Plain HTML/CSS | Simplest | Multi-page content sync becomes manual nightmare |
| No starter kit governance | Less overhead | Without AGENTS.md / ExecPlan discipline, agent output quality degrades over time |

## Consequences

### Positive
- Sub-1s page loads globally (Cloudflare edge + static HTML)
- $0/month hosting cost
- Agent can modify any page via markdown/MDX
- Full harness governance from day 1 (ExecPlan, review personas, pre-commit)
- Content is version-controlled in git (auditable, rollback-able)

### Negative
- Owner cannot edit content via browser UI (must go through agent or git)
- Astro ecosystem smaller than Next.js (fewer community plugins)
- Starter kit governance adds friction to first few PRs (learning curve)

### Monitoring
- If page load exceeds 3s in target regions → investigate Cloudflare caching
- If owner finds governance too heavy → simplify steering (remove unused personas)
- If Astro has breaking changes → pin version in package.json

## Retirement conditions

- If a CMS becomes necessary (e.g., owner hires a marketing team that needs browser editing) → migrate to Astro + Decap CMS or consider WordPress
- If Cloudflare Pages pricing changes → evaluate Vercel / Netlify
- If kiro.dev starter kit is superseded by a better framework → write ADR-0002
