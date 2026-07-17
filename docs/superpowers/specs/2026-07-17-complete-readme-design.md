# Complete README Design

## Goal

Make README.md the complete, standalone Chinese tutorial for sharing an OpenCodex service with Codex on another trusted LAN computer.

## Content

README will include the existing tutorial's purpose, principle, Mermaid architecture diagram, A/B quick instructions, A-computer setup, B-computer setup, connectivity validation, troubleshooting, minimal diagnostics, and an external-facing explanation.

The English portion remains a compact project description with a link to the Chinese README because the operational instructions are Windows-specific and Chinese is the target tutorial language.

## Attribution

README will include a visible `## 致谢与上游项目` section directly below the title. It will state that the guide is based on OpenCodex and link to https://github.com/lidge-jun/opencodex. The final acknowledgement section will repeat the attribution in English.

## Document Relationship

README.md becomes the canonical public guide. LAN-CODEX-TUTORIAL.md stays as a mirrored standalone copy for users who prefer a separate tutorial file.

## Safety Boundaries

- Use only placeholders for host IP addresses and tokens.
- Do not include real credentials, account details, or local usernames.
- State that this is for trusted LAN use and must not be exposed directly to the public internet.

## Verification

- README contains all primary tutorial sections and both quick instruction blocks.
- README has the visible upstream attribution link.
- All Markdown links target existing local files or the upstream repository.
- Credential scan of the staged Markdown files returns no matches.
