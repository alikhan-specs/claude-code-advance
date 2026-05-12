---
type: project
created: 2026-05-04
updated: 2026-05-12
status: active-research
side: personal
phase: research-clone
tags: [personal, claude-code, research, fork, agentic-ai, reference]
linked: [[claude-code-research]], [[jarvis]], [[ali-claude-starter-kit]]
---

# Claude Code Advance — Context

## 1. What it is
Personal research clone of the **publicly exposed Claude Code source snapshot** that became accessible on 2026-03-31 via npm source map exposure. The repo mirrors `@anthropic-ai/claude-code` source (~1,900 files, 512K+ lines TypeScript) for **educational and defensive security research** into agentic developer tooling architecture. Includes a `backup` branch with the original unmodified source, plus an MCP Explorer Server (`claude-code-explorer-mcp` on npm) for query-based exploration.

## 2. Why it exists
Two reasons:
- **Understand the runtime Ali is building on** — Jarvis and Holidai both run on the Anthropic Agent SDK / Claude Code runtime. Reading the real source (rather than the public docs) gives Ali stronger architectural conviction when designing his own agent systems.
- **Defensive security research surface** — the npm source-map exposure is a textbook supply-chain case study. Studying it (and the response) informs how Ali should think about agentic supply-chain risk inside TUI.

## 3. Where it lives
| | |
|---|---|
| **Vault** | `30-projects/claude-code-advance/` (submodule) |
| **Remote** | `github.com/alikhan-specs/claude-code-advance` |
| **Upstream snapshot** | `github.com/nirholas/claude-code` (the exposed source archive) |
| **Side** | Personal — public repo, no IP concerns (source already public) |
| **npm package** | `claude-code-explorer-mcp` (MCP server for querying this codebase) |

## 4. Tech stack (of the source under study)

| Layer | Tech |
|---|---|
| Language | TypeScript (512K+ lines) |
| Runtime | Bun |
| UI | React + Ink (terminal UI) |
| File count | ~1,900 source files |
| Notable deps | `@anthropic-ai/sdk`, `@anthropic-ai/sandbox-runtime`, `@aws-sdk/client-bedrock-runtime`, `@commander-js/extra-typings`, `@growthbook/growthbook`, `@modelcontextprotocol/sdk`, `@opentelemetry/api` |

## 5. Current state (as of 2026-05-12)

**Active research.** Last commit `8d3b01b fix: remove case-conflict tracking of skeleton.tsx` (2026-05-06). Recent activity:
- Refactored tool tests + added core tools validation
- README clarity pass
- Integration tests for Anthropic API + MCP server
- Unit tests for feature flags, macro properties, commands, and tools

The MCP Explorer Server is published to npm (`claude-code-explorer-mcp`) — anyone can install it and query the Claude Code source structure via an MCP-compatible client (e.g. Claude Desktop).

## 6. Recent decisions
- **Public fork of public repo** — no IP concerns; the source is already public. Personal GitHub side per two-GitHub rule.
- **MCP Explorer Server as the primary research artefact** — rather than just reading code statically, built a query interface so the research is reusable and shareable.
- **Backup branch preserves original** — modifications happen on `main`; `backup` keeps the unmodified snapshot for reference and integrity.
- **Sister repo split (2026-05-04)** — created [[claude-code-research]] as a parallel clone of `instructkr/claude-code` for cross-reference research. Two snapshots, two perspectives.

## 7. Open threads / blockers
- **Upstream evolution unclear** — `nirholas/claude-code` may or may not stay in sync with Anthropic releases. Tracking strategy not decided.
- **Research outputs not consolidated** — findings live in this repo's commits and README; none have flowed back into a vault `consolidated/` note yet. Worth a 30-minute synthesis pass.
- **Legal exposure assessment** — public source from npm exposure, but defensive use only. Worth a quick sanity check that the research-use framing is robust.

## 8. What "done" looks like
Research projects don't finish. Done-shaped milestones:
- Findings consolidated into a vault `20-memory/consolidated/claude-code-internals.md` note
- MCP Explorer Server stable + documented + adopted by at least one other researcher
- Architectural patterns from the source explicitly cited in Jarvis design decisions

## 9. People involved
- Ali — sole researcher + maintainer
- npm users of `claude-code-explorer-mcp` — anonymous

## 10. Cross-references
- Related vault: [[claude-code-research]] (sibling research clone), [[jarvis]] (consumer of architectural insights), [[ali-claude-starter-kit]] (governance patterns informed by what works in Claude Code itself)
- Strategic narrative: agentic supply-chain research — Ali walks the talk on understanding the runtime before scaling it inside TUI
- Related consolidated notes: `20-memory/consolidated/secure-agentic-design.md`

## 11. How to work on this with the clone
Project root has its own README, integration tests, and an MCP server. The vault `_context.md` is the strategic-position view. When researching specific Claude Code internals, prefer the MCP Explorer Server interface over raw file reads where possible — it's the persistent query layer.
