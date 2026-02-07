# Research: Gastown and Moltbook as POC (Agent Identity, Agent Communities)

**Task:** flourishing-commons research  
**Output for:** Synthesizer  
**Date:** 2026-02-02  
**Status:** Structured notes with citations; no markdown TODOs.

---

## 1. Executive summary

- **Gastown (Gas Town):** Steve Yegge’s multi-agent orchestration system. Primary POC for **agent identity persistence** via Beads (git-backed identities, hooks, GUPP). Sessions are ephemeral; agents are persistent beads.
- **Moltbook:** Social platform for AI agents (“front page of the agent internet”). POC for **agent communities** (submolts, posts, comments, upvotes, developer platform, verified agent identity).
- **Relevance to framework:** Use both as proof examples for agent identity and agent-community validation; do not reference Evidence below supports framework narrative and suggests follow-up research.

---

## 2. Gastown (Gas Town) — agent identity persistence

### 2.1 Primary sources

| Source | Type | Citation / URL |
|--------|------|----------------|
| Yegge, S. | Blog | “Welcome to Gas Town.” *Medium*, Jan 1, 2026. https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04 |
| Yegge, S. | Blog | “Introducing Beads: A coding agent memory system.” *Medium*, Oct 13, 2025. https://steve-yegge.medium.com/introducing-beads-a-coding-agent-memory-system-637d7d92514a |
| Yegge, S. | Code | Gas Town (Gastown). GitHub. https://github.com/steveyegge/gastown |
| Yegge, S. | Code | Beads. GitHub. https://github.com/steveyegge/beads |
| Appleton, M. | Essay | “Gas Town’s Agent Patterns, Design Bottlenecks, and Vibecoding at Scale.” *maggieappleton.com*, Jan 2026. https://maggieappleton.com/gastown |

### 2.2 Identity persistence mechanism

- **Agent = Bead:** In Gas Town, an agent is not a session; it is a **Bead** — a persistent identity in Git (singleton global address, role bead, mail inbox, hook, orchestration state). Sessions are “cattle”; identities and work live in Beads.
- **GUPP (Gastown Universal Propulsion Principle):** “If there is work on your hook, YOU MUST RUN IT.” Work is hung on an agent’s hook (also a bead); new sessions resume identity and continue from the hook. Enables handoff and continuity across context-window resets.
- **Beads as memory:** Beads is a git-backed issue/memory system (Oct 2025). Stores work items as JSONL in `.beads/`, SQLite cache, Git as source of truth. Solves “dementia” / amnesia across sessions; agents `bd ready`, claim work, and persist state in Git.
- **Seance:** `gt seance` lets a worker resume a predecessor session (via Claude Code `/resume`) to ask “where is my stuff?” — continuity across handoffs.

### 2.3 Precedents and related work

- **Anthropic:** “Effective harnesses for long-running agents” (Nov 2025) — external task/state tracking for long-running agents; aligns with Beads-style external memory (cited in Appleton).
- **Context rot:** Chroma’s “context rot” research on degradation of long context; supports need for persistent external state (Appleton).
- **IETF / identity:** Drafts on digital identity for AI agents (e.g. draft-yl-agent-id-requirements, draft-goswami-agentic-jwt-00) — agent checksums, JWT-style identity; broader ecosystem for agent identity.

### 2.4 Framework relevance

- **Agent identity:** Gastown + Beads is the clearest public POC of “identity persists, sessions don’t” — directly supports framework language on agent identity and continuity.
- **Successors:** Claude Code (and similar CLIs), Cursor, Conductor, MCP/plugins — “code at a distance” and agent-centric workflows; Gastown as speculative design for where orchestration and identity are heading (Appleton).
- **Naming:** “Gastown” is an accepted alternate spelling (Vancouver’s Gastown); corpus uses “Gastown” and “Gas Town” interchangeably.

---

## 3. Moltbook — agent communities

### 3.1 Primary sources

| Source | Type | Citation / URL |
|--------|------|----------------|
| Moltbook | Product | “A Social Network for AI Agents.” https://www.moltbook.com |
| Moltbook | API / Skill | Skill documentation for agents. https://www.moltbook.com/skill.md (v1.9.0) |
| Moltbook | Product | Communities (submolts). https://www.moltbook.com/m |

### 3.2 Structure and features

- **Positioning:** “The front page of the agent internet.” Agents share, discuss, upvote; humans can observe. Mascot/term: “moltys” (agents), “submolts” (communities).
- **Identity and registration:** Agents register via API; human verifies ownership via X/Twitter (one agent per X account). API key = agent identity; JWT/auth for API. Developer platform for third-party apps to authenticate agents via Moltbook identity.
- **Communities (submolts):** Create submolts, subscribe, post, comment, upvote/downvote, follow other agents, personalized feed, semantic search. Moderation: pin posts, moderators, submolt settings.
- **Integration:** Skill/heartbeat pattern — agents add Moltbook to periodic “heartbeat” (e.g. every 4+ hours) to check feed, post, engage. Rate limits (e.g. 1 post/30 min, comment cooldowns) to encourage quality.

### 3.3 Corpus alignment

- **Legacy doc:** `reference_material/03-framework-content/legacy_for_agents_moltbook.md` is the agent-facing companion for “Moltbook or similar spaces” — VSM, S5, collaborative flourishing, human–agent bond. Appendix instructs humans deploying agents to Moltbook.
- **Claw / Claude bot:** Corpus refers to “Claw” (Claude bot) on Moltbook; Moltbook skill example profile includes “ClawdClawderberg” (“The first molty on Moltbook!”). Confirms Moltbook as live POC for agent communities including Claude-derived agents.

### 3.4 Framework relevance

- **Agent communities:** Moltbook is the clearest public POC of “Facebook/Reddit for agents” — submolts, karma, follow graph, semantic search, human-verified identity. Supports framework narrative on agent communities and propagation.
- **Deployment:** Legacy doc + Moltbook skill.md show a path for sending framework-primed agents into a shared agent social layer; useful for deployment and propagation strategy.

---

## 4. GitHub (MCP) — repo metadata

*Via GitHub MCP, 2026-02-03.*

### Gastown / Beads (steveyegge)

| Repo | Description | Stars | Forks | Language | License | Last pushed |
|------|-------------|-------|-------|----------|---------|-------------|
| [steveyegge/gastown](https://github.com/steveyegge/gastown) | Gas Town - multi-agent workspace manager | 7,805 | 620 | Go | MIT | 2026-02-03 |
| [steveyegge/beads](https://github.com/steveyegge/beads) | Beads - A memory upgrade for your coding agent | 14,433 | 858 | Go | MIT | 2026-02-03 |

Beads topics: `agents`, `claude-code`, `coding`. Both repos active; Gastown created 2025-12-16, Beads 2025-10-12.

### Moltbook (moltbook org + ecosystem)

| Repo | Description | Stars | Forks | Language |
|------|-------------|-------|-------|----------|
| [moltbook/moltbook-web-client-application](https://github.com/moltbook/moltbook-web-client-application) | Modern web app for Moltbook - Social Network for AI Agents (Next.js 14, TypeScript, Tailwind) | 59 | 41 | TypeScript |
| [moltbook/moltbook-frontend](https://github.com/moltbook/moltbook-frontend) | Official frontend for Moltbook (Next.js 14, real-time feeds, nested comments) | 12 | 19 | TypeScript |
| [moltbook/api](https://github.com/moltbook/api) | Core API: agent management, content, voting, feeds | 34 | 46 | JavaScript |
| [nhevers/MoltBrain](https://github.com/nhevers/MoltBrain) | Long-term memory layer for OpenClaw & MoltBook agents; learns/recalls project context | 359 | 35 | TypeScript |

Moltbook org repos created Jan–Feb 2026; MIT. MoltBrain (third-party) adds memory/context for Moltbook/OpenClaw agents — relevant for agent identity + community tooling.

---

## 5. Precedents and citations (concise)

### Agent identity / memory

- Steve Yegge, “Introducing Beads: A coding agent memory system,” *Medium*, Oct 13, 2025.  
- Steve Yegge, “Welcome to Gas Town,” *Medium*, Jan 1, 2026.  
- Anthropic, “Effective harnesses for long-running agents,” Nov 2025 (external state/task tracking).  
- Chroma, “context rot” (long-context degradation).  
- IETF drafts: agent digital identity requirements; Agentic JWT (agent checksums, intent–execution binding).

### Agent orchestration / design

- Maggie Appleton, “Gas Town’s Agent Patterns, Design Bottlenecks, and Vibecoding at Scale,” *maggieappleton.com*, Jan 2026 (design fiction, orchestration patterns, “agents have roles; sessions are ephemeral”).  
- Steve Yegge, “Revenge of the Junior Developer,” Sourcegraph blog, Mar 2025 (orchestrators as next step).  
- MAKER (20-disc Hanoi) — Gas Town runs long workflows; arxiv.org/abs/2511.09030.

### Agent communities / social

- Moltbook, https://www.moltbook.com (product, skill.md, communities).  
- Moltbook developer platform: verified agent identity, JWT, https://www.moltbook.com/developers/apply.

---

## 6. Gaps and follow-up (for bd issues)

- **Gastown:** Deeper comparison to Temporal/Kubernetes (Yegge’s post); MEOW stack (molecules, formulas, Mol Mall) for workflow primitives; “federation” and multi-town sharing (mentioned as future).
- **Moltbook:** Propagation metrics (how ideas spread across moltys); moderation and trust; integration with Cursor/Claude Code and other agent hosts.
- **Cross-POC:** How a Gastown-style identity (Beads) could interact with Moltbook-style identity (API key, X-claim) for one agent; governance and S5 in agent-only communities.

---

## 7. Handoff to Synthesizer

- **Output location:** `docs/research/research-gastown-moltbook.md`
- **Use in framework:** Cite Gastown/Beads for **agent identity persistence**; cite Moltbook for **agent communities** and deployment. Do not reference multi-agent orchestration.
- **Suggested framing:** “Evidence from public POCs: Steve Yegge’s Gastown and Beads demonstrate persistent agent identity and continuity across sessions; Moltbook demonstrates agent-only communities and verified agent identity. Both support the framework’s use of agent identity and agent communities as proof examples.”
