# GitHub Naming Convention — ixruby & vishnu-madhavan-git

Single source of truth for professional repo hygiene. Every new repo must follow this.

## 1. Org `ixruby` — Brand & Product (long-term)

| Pattern | Example | When |
|---------|---------|------|
| `9ruby-<service>` | `9ruby-site` (www.9ruby.com), `9ruby-core`, `9ruby-ui`, `9ruby-automation` | Brand services — keep split, not monorepo until Phase 2 |
| `ruby-<platform>` | `ruby-os`, `ruby-automation-os` | Platform/infra (shared) |
| `<product>` | `9money`, `nexlyn`, `novavox` | Standalone products |
| `pc-backup-*` | — | **BANNED** — use single `vishnu-madhavan-git/ruby-system-backup` |
| `v0-*/aura-*` | — | Experiments → **archive** after 30 days inactive |

**Rules:**
- `kebab-case`, lowercase, no underscores, no dots
- Default branch `main` (not `master`), protected: require `CI` check (`check` context), no force push
- Topics: `9ruby`, `nextjs`/`vercel` etc. + description with homepage link
- Vercel deploys via Git integration (push to `main` = production), preview per PR — no custom deploy Action

## 2. Personal `vishnu-madhavan-git` — Private & Clients

| Pattern | Example |
|---------|---------|
| `<project>` | `leaforia`, `company-os` |
| `<client>-<project>` | `acrylic-mirrors` |

- Keep ≤10 active personal repos; archive bulk backups immediately
- Client work should move to `ixruby` when shared

## 3. Branch & Workflow

- `main` = production, feature branches `feat/`, `fix/`, `chore/`
- `.github/workflows/ci.yml` → `npm ci → lint → build` (Vercel still deploys)
- `delete_branch_on_merge: true`, squash merge

## 4. Archive Policy

- `pc-backup-*` → archived (118 done Aug 27, kept `ruby-system-backup`)
- `v0-*/aura-*/dreaming` etc. → archive after 30 days no push (30 done Aug 27)
- Search still works on archived repos, just not in active list

## 5. Phase 2 (next)

Merge `9ruby-site+core+ui+automation` into monorepo `ixruby/9ruby` with `apps/www`, `packages/ui` — single CI, atomic deploys. Do after `main` protection is green.

---
*Enforced Aug 27 2026 — Hermes + Vercel Git integration is source of truth.*