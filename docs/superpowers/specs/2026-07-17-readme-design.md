# README Design

## Goal

Create a concise, bilingual repository homepage for the OpenCodex LAN Codex guide. It should explain the project at a glance and route readers to the complete Chinese tutorial without duplicating its detailed configuration steps.

## Audience

- Chinese-speaking users who want to share one OpenCodex instance with Codex on another LAN device.
- International visitors who need a short English explanation and a clear link to the full guide.

## Structure

1. Project title and one-sentence summary.
2. A Mermaid diagram showing Computer B's Codex requests flowing to Computer A's OpenCodex and then to configured providers.
3. Chinese quick-start section with the key prerequisite and a link to the full tutorial.
4. English quick-start section with the same scope and link.
5. Security note: keep the API token private and expose the service only on trusted LANs.
6. Acknowledgement and link to lidge-jun/opencodex.

## Content Boundaries

- README is bilingual but intentionally brief.
- The full setup commands, troubleshooting, and operational details remain in LAN-CODEX-TUTORIAL.md.
- No real IP addresses, tokens, account names, local paths, or credential examples are included.
- No generated image assets are needed; the Mermaid diagram keeps the repository lightweight and readable on GitHub.

## Verification

- Confirm README renders as valid Markdown and includes working relative links.
- Scan staged public files for credential-like strings before publishing.
