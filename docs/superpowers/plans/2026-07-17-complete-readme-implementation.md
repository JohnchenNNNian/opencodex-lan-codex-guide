# Complete README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Turn README.md into a complete standalone LAN OpenCodex tutorial and prominently cite the upstream project.

**Architecture:** README.md contains the complete Chinese tutorial structure currently held in LAN-CODEX-TUTORIAL.md, preceded by a visible upstream acknowledgement. LAN-CODEX-TUTORIAL.md remains a mirror. The short English material remains an introductory note only.

**Tech Stack:** GitHub Flavored Markdown and Mermaid.

## Global Constraints

- Include no real IP address, token, account name, local path, or credential example.
- Link visibly to https://github.com/lidge-jun/opencodex.
- Preserve A/B quick instructions, setup, validation, troubleshooting, and safety guidance.

---

### Task 1: Expand and publish the standalone README

**Files:**
- Modify: `README.md`
- Verify: `README.md`, `LAN-CODEX-TUTORIAL.md`

**Interfaces:**
- Consumes: The complete tutorial content in `LAN-CODEX-TUTORIAL.md`.
- Produces: A standalone `README.md` that a reader can follow without opening another file.

- [ ] **Step 1: Rebuild README from the full tutorial**

Replace the abbreviated README body with the full Chinese guide: acknowledgement, suitability, principle, quick A/B instructions, architecture, A configuration, B configuration, validation, troubleshooting, minimal diagnostics, external explanation, and summary. Include the upstream repository link in the first acknowledgement section and an English note near the end.

- [ ] **Step 2: Verify completeness and safety**

Run:

```powershell
git add -- README.md
git diff --cached --check
Select-String -LiteralPath README.md -Pattern '^## A 电脑配置|^## B 电脑配置|^## 验证是否成功|^## 常见问题|lidge-jun/opencodex'
Select-String -LiteralPath README.md -Pattern '(?i)(refresh_token|client_secret|sk-[a-z0-9]{10,})'
```

Expected: all required sections and the upstream link are present; the Markdown check succeeds; the credential scan has no matches.

- [ ] **Step 3: Commit and push**

Run:

```powershell
git commit -m "Expand README into complete LAN guide"
git push origin main
```

Expected: Git reports a new commit and successful push to `origin/main`.
