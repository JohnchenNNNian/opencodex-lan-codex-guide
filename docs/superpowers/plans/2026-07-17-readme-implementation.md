# README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a concise bilingual README that explains the OpenCodex LAN-sharing guide and links to the detailed tutorial.

**Architecture:** README.md is the public landing page. It contains a compact Mermaid flow, Chinese and English quick-start sections, security boundaries, and acknowledgement. LAN-CODEX-TUTORIAL.md remains the single source for detailed setup and troubleshooting.

**Tech Stack:** GitHub Flavored Markdown and Mermaid.

## Global Constraints

- Include no real IP address, token, account name, local path, or credential example.
- Keep the full operational instructions in LAN-CODEX-TUTORIAL.md.
- Use relative links that render on GitHub.

---

### Task 1: Create and publish the README

**Files:**
- Create: `README.md`
- Verify: `README.md`, `LAN-CODEX-TUTORIAL.md`

**Interfaces:**
- Consumes: `LAN-CODEX-TUTORIAL.md` as the detailed guide linked from README.
- Produces: `README.md` as the bilingual GitHub landing page.

- [ ] **Step 1: Create the public README**

Write `README.md` with this fixed structure: title and summary; a Mermaid request-flow diagram; Chinese quick start; English quick start; security note; link to `LAN-CODEX-TUTORIAL.md`; acknowledgement linking to `https://github.com/lidge-jun/opencodex`.

- [ ] **Step 2: Verify the staged public files**

Run:

```powershell
git add -- README.md
git diff --cached --check
Select-String -LiteralPath README.md,LAN-CODEX-TUTORIAL.md -Pattern '(?i)(refresh_token|client_secret|sk-[a-z0-9]{10,})'
```

Expected: `git diff --cached --check` returns exit code 0 and the credential scan has no matches.

- [ ] **Step 3: Commit and push**

Run:

```powershell
git commit -m "Add bilingual project README"
git push origin main
```

Expected: Git reports the new commit and a successful push to `origin/main`.
