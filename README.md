# Solo Engineer Project Checklist (2026)

Run through this for every new project, or as a hardening pass on an existing one.

## 1. Development workflow
- [ ] Agentic coding tool in use (opencode, Claude Code, etc.)
- [ ] Spec-driven development (openspec or equivalent) before major features
- [ ] Agent skills / reusable prompts for common engineering tasks
- [ ] Automated tests (unit + integration) required to pass before merge
- [ ] CI pipeline (GitHub Actions or equivalent) on every PR

## 2. Security — AI-generated code is untrusted by default
- [ ] SAST scanning as a **required** CI check (not advisory)
- [ ] Dependency / SCA scanning in CI
- [ ] Secret scanning on commits and history (revoke any leaked keys immediately)
- [ ] Dependencies pinned; new/unfamiliar packages verified before install (watch for hallucinated "slopsquatted" packages)
- [ ] Human review required on: auth flows, payment code, anything touching secrets or customer data
- [ ] Secrets manager in use (not loose `.env` files), especially since agents have filesystem access

## 3. Observability & reliability
- [ ] Uptime monitoring with alerts (phone/email)
- [ ] Error tracking (Sentry-style) — not just "is it up," but "why did it break and for whom"
- [ ] If running LLM/agent workflows in prod: agent-specific tracing (multi-step failures don't show up as normal HTTP errors)
- [ ] Basic logging you can actually query when something breaks

## 4. Deployment safety
- [ ] Preview/staging environment per PR
- [ ] Known, fast rollback path (tested, not theoretical)
- [ ] Reversible database migrations
- [ ] Backups — and an actual tested restore, not just "backups exist"

## 5. Dependency hygiene
- [ ] Automated dependency updates (Renovate/Dependabot) running regularly
- [ ] Periodic manual check for abandoned/high-risk dependencies

## 6. Business/non-code basics
- [ ] Terms of Service + Privacy Policy in place
- [ ] Basic compliance check if handling EU/CA users (GDPR/CCPA basics)
- [ ] Product analytics (PostHog or similar) wired in
- [ ] A short personal incident runbook ("if X breaks, check Y first") — you're the only on-call

## 7. Before calling a project "production ready"
- [ ] All of section 2 (security) checked
- [ ] All of section 3 (observability) checked
- [ ] Rollback tested at least once
- [ ] Backups restore-tested at least once
