# Quick Commands Design

## Goal

Add two copy-ready Chinese instructions near the top of the public documentation: one for configuring the OpenCodex host on Computer A and one for configuring the Codex client on Computer B.

## Placement

- README.md: directly after the Mermaid request-flow diagram and before the Chinese overview.
- LAN-CODEX-TUTORIAL.md: directly after the one-sentence principle and before the detailed architecture diagram.

## Command Content

### Computer A

The instruction is intended to be pasted into Codex on the OpenCodex host. It asks Codex to configure OpenCodex to listen on `0.0.0.0:10100`, use a user-provided API token, create a Windows inbound firewall rule, restart the service, and verify the local health endpoint. It uses `<YOUR_API_TOKEN>` as a required placeholder and tells the reader to replace it.

### Computer B

The instruction is intended to be pasted into Codex on the client computer. It asks Codex to set `OPENCODEX_API_AUTH_TOKEN`, configure the `opencodex` model provider with `http://<A_HOST_IP>:10100/v1`, remove conflicting root `openai_base_url` settings, ensure the model catalog path exists, restart Codex, and verify the providers endpoint. It uses `<A_HOST_IP>` and `<YOUR_API_TOKEN>` as required placeholders.

## Safety Boundaries

- Instructions must never contain real IP addresses, tokens, account names, or local user paths.
- They state that the token must be identical on both computers and must remain private.
- They are for a trusted LAN only and do not recommend public-internet exposure.

## Verification

- README and tutorial both contain A and B instruction headings before their detailed setup sections.
- Placeholder names match between files.
- A credential scan of the staged public Markdown files has no matches.
