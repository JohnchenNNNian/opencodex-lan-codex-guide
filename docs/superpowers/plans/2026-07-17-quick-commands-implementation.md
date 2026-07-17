# Quick Commands Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Put copy-ready Computer A and Computer B Codex instructions near the top of the README and full tutorial.

**Architecture:** README.md offers the public overview and the two instructions immediately after its architecture diagram. LAN-CODEX-TUTORIAL.md presents the same instruction pair before detailed explanations. Both use identical placeholder names and keep real credentials out of the repository.

**Tech Stack:** GitHub Flavored Markdown.

## Global Constraints

- Include no real IP address, token, account name, local path, or credential example.
- Use `<A_HOST_IP>` and `<YOUR_API_TOKEN>` in both documents.
- State that the service is for a trusted LAN and that the token is private.

---

### Task 1: Add and publish the two quick instructions

**Files:**
- Modify: `README.md`
- Modify: `LAN-CODEX-TUTORIAL.md`
- Verify: `README.md`, `LAN-CODEX-TUTORIAL.md`

**Interfaces:**
- Consumes: Existing OpenCodex service configuration details and the `opencodex` provider format already documented in the tutorial.
- Produces: Matching A and B copy-ready instruction blocks at the top of both public documents.

- [ ] **Step 1: Add the A and B instruction blocks**

Insert a `## 快速使用：把下面两段分别发给 A、B 电脑上的 Codex` section after README's Mermaid block and after the tutorial's one-sentence principle. Add `### A 电脑` and `### B 电脑` text blocks. The A block specifies `0.0.0.0:10100`, Windows Firewall, a health check, and `<YOUR_API_TOKEN>`. The B block specifies `OPENCODEX_API_AUTH_TOKEN`, `model_provider = "opencodex"`, `http://<A_HOST_IP>:10100/v1`, removal of root `openai_base_url`, catalog availability, restart, and a providers endpoint check.

- [ ] **Step 2: Verify layout, placeholders, and public safety**

Run:

```powershell
git add -- README.md LAN-CODEX-TUTORIAL.md
git diff --cached --check
Select-String -LiteralPath README.md,LAN-CODEX-TUTORIAL.md -Pattern '<A_HOST_IP>|<YOUR_API_TOKEN>'
Select-String -LiteralPath README.md,LAN-CODEX-TUTORIAL.md -Pattern '(?i)(refresh_token|client_secret|sk-[a-z0-9]{10,})'
```

Expected: the Markdown check succeeds, each placeholder appears in both files, and the credential scan has no matches.

- [ ] **Step 3: Commit and push**

Run:

```powershell
git commit -m "Add LAN setup quick commands"
git push origin main
```

Expected: Git reports a new commit and successful push to `origin/main`.
