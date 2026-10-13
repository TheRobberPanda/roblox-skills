# Hussball — ROADMAP

Single source of next work. Built with Claude Code and the `roblox-skills` lifecycle (`.claude/skills/roblox-skills`). Section numbers (§) refer to `game-design-docs/18_hussball_gdd.html`.

**Current phase:** 1 — Market and concept
**Next buildable milestone:** 1.2 (PRD)

## How to read this file

- `[ ]` not started
- `[~]` built and tested, waiting for human approval
- `[x]` implemented, tested or playtested, and explicitly approved by a human. Add the date only after approval.
- `AFK` Claude can build and verify it alone.
- `HITL` needs a human: a design call, a Studio action, a playtest, a purchase test, or an art approval.
- Each item is one playtestable slice. Build in order unless a human redirects.

## Project rules (override the skills where they conflict)

1. **Blockbench rule (GDD §2.1).** Claude and the Roblox MCP never create game art. Do not use `generate_mesh`, `generate_material`, or `generate_procedural_model` from `roblox-asset-pipeline` for characters, ball, animations, UI art, sounds, or map parts. Humans author those in Blockbench.
2. **Placeholder rule (GDD §2.3).** Any unrenamed placeholder blocks launch. The release check must fail on one.
3. **Server authority.** Currency, inventory, purchases, rewards, progression, and aura are server-owned from the first slice.
4. **UI gate.** No UI slice becomes buildable until its design artifact (`roblox-game-ux`) is approved. Until then, mark it `HITL`.
5. **Creator Store imports.** Audit with `roblox-creator-store-security-audit` before trusting or enabling scripts.

---

## Phase 1 — Market and concept

- [ ] **1.1** Validate audience (ages 10–15) and success metrics — `HITL` · §1.4, §21
- [ ] **1.2** Write the PRD from the GDD — `AFK` · skill: `roblox-to-prd` · output: `roadmap/hussball/prd.md`
- [ ] **1.3** Write the first-30-seconds script and core loop test — `HITL` · §1.2, §3.6
- [ ] **1.4** Resolve open items and write GDD revision 12 — `HITL` · §26
  - Reward rule for players who stay when a teammate leaves (§3.5)
  - Emote detection feasibility (§10.3)
  - Blockbench export format (§2.2)
  - Randomized item policy (§13.1) and Robux pricing (§17.1)
  - Slip thresholds, to set in playtests (§4.2)
- [ ] **1.5** Convert the PRD into vertical slices — `AFK` · skill: `roblox-to-issues`
- [ ] **1.6** Triage all slices into `ready-to-build` or `needs-human` — `HITL` · skill: `roblox-triage`

**Gate:** PRD approved, every Phase 2 slice is `ready-to-build`.

## Phase 2 — Prototype (core combat)

- [ ] **2.1** Scaffold repo: Rojo, Wally, Selene, StyLua, CI — `AFK` · skill: `roblox-luau-architecture`
- [ ] **2.2** Asset folders and placeholder release-check script — `AFK` · §2.2, §2.3
- [ ] **2.3** Spike: owned-emote detection and playback — `HITL` · §10.3
- [ ] **2.4** Spike: Blockbench import and frame timing — `HITL` · §2.2
- [ ] **2.5** Spike: text filter on chat and reaction paths — `AFK` · §21.1
- [ ] **2.6** Spike: server-owned ball feel, two clients — `HITL`
- [ ] **2.7** Tracer bullet: server ball, throw with charge, 50% default throw — `AFK` · §5
- [ ] **2.8** Tether and lock past 100% — `AFK` · §5.3, §5.5
- [ ] **2.9** Movement with inertia and slip — `AFK` · §4
- [ ] **2.10** Catch and save — `AFK` · §6
- [ ] **2.11** Dodge cooldown, 0.20 s floor window, huss, and shared sound — `AFK` · §6.2–6.3, §44 #1–2
- [ ] **2.12** Hit, slow state, and graveyard — `AFK` · §7, §8
- [ ] **2.13** 2v2 reaction-budget playtest — `HITL` · §44 #1

**Gate:** 2v2 match runs with reaction-budget timing working.

## Phase 3 — Vertical slice

- [ ] **3.1** Season 1 gymnasium with placeholder geometry — `AFK` · §9.1 (art by human, §2.1)
- [ ] **3.2** 3-second map intro that doesn't block input — `AFK` · §3.6
- [ ] **3.3** Basic 5v5 queue — `AFK` · §16
- [ ] **3.4** 5-minute match timer and win check — `AFK` · §3.7
- [ ] **3.5** Team-size speed boost, +5% per missing player — `AFK` · §3.5, §44 #14
- [ ] **3.6** No late joins, no rejoin — `AFK` · §3.4, §44 #13
- [ ] **3.7** 60 s overtime, revives off, dead players can't touch the ball — `AFK` · §3.7, §44 #11
- [ ] **3.8** Draw result when overtime ends with multiple teams alive — `AFK` · §44 #12
- [ ] **3.9** Dead-player roaming, ball recovery, 1 s throw — `AFK` · §8
- [ ] **3.10** First-person (PC) and third-person (console, mobile) cameras — `HITL` · §28
- [ ] **3.11** Full 5v5 end-to-end playtest — `HITL` · §3

**Gate:** full 5v5 match plays end to end with no placeholders in the flow.

## Phase 4 — Production, Alpha

- [ ] **4.1** Revive rules: kill revives one teammate, touch does not — `AFK` · §7.3, §44 #9–10
- [ ] **4.2** Round-end vote: three cards, 10 s timer, skip — `HITL` until UI approved · §11
- [ ] **4.3** Reward reveal in two carousels — `HITL` until UI approved · §13.2
- [ ] **4.4** Hidden feat points and feat tracking — `AFK` · §13.4
- [ ] **4.5** MVP selection and MVP music — `AFK` · §13.5, §44 #15
- [ ] **4.6** Server-side aura calculation, numbers never shown — `AFK` · §12, §44 #19
- [ ] **4.7** End-of-match aura display and toggle — `HITL` until UI approved · §12.5–12.6, §44 #18
- [ ] **4.8** PE teacher ejection and invader grab — `AFK` · §3.3, §8.3
- [ ] **4.9** Emote detection and compact replays — `AFK` · §10 · depends on 2.3
- [ ] **4.10** Profile persistence: session locking, schema versioning, autosave, `BindToClose` — `AFK` · skill: `roblox-datastore-persistence` · §19
- [ ] **4.11** Server validation and rate limits on every remote — `AFK` · skill: `roblox-security-economy` · §20
- [ ] **4.12** Acceptance tests 1–20 automated — `AFK` · §44

**Gate:** all acceptance tests 1–20 pass.

## Phase 5 — Production, Beta

- [ ] **5.1** Tickets and duplicate conversion by category and rarity — `AFK` · §14, §15, §44 #17
- [ ] **5.2** Battle pass with season tiers — `HITL` (economy) · §15
- [ ] **5.3** Gymnasium shop, purchase rules, 24 h feat-buy window — `AFK` · skill: `roblox-monetization-optimization` · §17, §44 #16
- [ ] **5.4** Cosmetics catalog — `AFK` · §18 · audit any third-party imports
- [ ] **5.5** Animation teachers — `HITL` (animation by human) · §14.2
- [ ] **5.6** Walkable spectator matches and spectator area — `AFK` · §3.2
- [ ] **5.7** Spectator bubbles, team aura visual, cosmetic-only spectator throws — `AFK` · §3.2
- [ ] **5.8** Boards and compare machine — `HITL` until UI approved · §12.7–12.8
- [ ] **5.9** Chat, quick-reaction wheel, reaction sounds — `AFK` · skill: `roblox-social-systems` · §30
- [ ] **5.10** Dynamic music, replacing AI tracks — `HITL` · §29
- [ ] **5.11** Report flow and moderation tools — `AFK` · skill: `roblox-policy-compliance` · §43
- [ ] **5.12** Analytics events — `AFK` · skill: `roblox-analytics-instrumentation` · §41
- [ ] **5.13** Localization — `AFK` · skill: `roblox-localization-accessibility` · §40

**Gate:** playtests show no timing or balance blockers.

## Phase 6 — Internal QA and security

- [ ] **6.1** Multi-client playtest matrix — `HITL` · skill: `roblox-playtest-qa`
- [ ] **6.2** Mobile playtest and performance budget — `HITL` · skill: `roblox-mobile-playtest`, `roblox-performance-optimization`
- [ ] **6.3** Purchase tests in Studio using test mode — `HITL`
- [ ] **6.4** Creator Store and third-party import audit — `AFK` · skill: `roblox-creator-store-security-audit`
- [ ] **6.5** Policy compliance check — `AFK` · skill: `roblox-policy-compliance`

**Gate:** mobile, performance, purchases, DataStores, remotes, and imports all pass.

## Phase 7 — Soft launch (closed playtest)

- [ ] **7.1** Analytics live for closed testers — `AFK`
- [ ] **7.2** Closed playtest wave 1 — `HITL` · skill: `roblox-release-operations`
- [ ] **7.3** Triage tester feedback — `HITL` · skill: `roblox-triage`
- [ ] **7.4** Tuning until no timing or balance blockers remain — `HITL` · §32

**Gate:** tester feedback triaged, top retention leaks addressed.

## Phase 8 — Polish and balance

- [ ] **8.1** Onboarding and tutorial — `HITL` until UI approved · §35 · skill: `roblox-game-ux`
- [ ] **8.2** Disconnect and edge-case handling — `AFK` · §36
- [ ] **8.3** Audio polish, including the huss sound — `HITL` · §37 · skill: `roblox-animation-audio-feedback`
- [ ] **8.4** Balance pass — `HITL` · skill: `roblox-economy-balancing`
- [ ] **8.5** Code cleanup and refactor — `AFK` · skill: `roblox-code-maintenance-refactor`

## Phase 9 — Publishing and launch

- [ ] **9.1** Policy review: randomized items and Robux pricing — `HITL` · §13.1, §17.1
- [ ] **9.2** Store page and thumbnails — `HITL` · skill: `roblox-publishing-discovery`
- [ ] **9.3** Release notes and rollback plan — `AFK` · skill: `roblox-release-operations`
- [ ] **9.4** Replace every placeholder, then pass the release gate — `HITL` · §2.3, §31.1
- [ ] **9.5** Soft launch of season 1 — `HITL`
- [ ] **9.6** Full launch of season 1 — `HITL`

**Gate:** release gate passes with no placeholders.

## Phase 10 — Live ops

- [ ] **10.1** Season cadence: a new map, battle pass, and cosmetics every 8 weeks — `HITL` · §31.4 · skill: `roblox-liveops-roadmap`
- [ ] **10.2** Day 1, 3, and 7 retention hooks — `AFK` · skill: `roblox-retention-monetization`
- [ ] **10.3** Remaining Gymnasium NPCs: DJ, young huss, ball painter, canvas, tongue — `HITL` · §14
- [ ] **10.4** Balance patches from analytics — `HITL` · skill: `roblox-economy-balancing`

## Phase 11 — Maintenance and growth

- [ ] **11.1** Bug triage loop — `HITL` · skill: `roblox-triage`, `roblox-debugging-bugfix`
- [ ] **11.2** Admin tools and observability — `AFK` · skill: `roblox-admin-tools-observability`
- [ ] **11.3** Growth iteration — `HITL` · skill: `roblox-growth-marketing`
- [ ] **11.4** Later maps and seasons, repeating from 10.1 — `HITL`
