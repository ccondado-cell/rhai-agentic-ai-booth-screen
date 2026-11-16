# Design Brief: re:Invent Booth Screen, "Agents Worth Trusting"

**Deliverable:** one self-contained HTML file (`index.html`). No build tools, no framework, no external requests.
**Purpose:** dual-mode booth screen. Mode A is an auto-advancing attract loop for TVs facing foot traffic. Mode B is a presenter-controlled click-through for a 10 to 12 minute mini-theater talk. Same scenes, same file.
**Design constraint hierarchy:** design for the 3-second glance first (the loop is the harder medium); the presenter mode inherits the result. If a scene needs explaining to be understood, it has too many words.

---

## 1. The two modes

**Mode A: Attract loop (default on load)**
- Auto-advance through all 16 scenes, 6.4 seconds each, then restart seamlessly. Total loop: 102.4 seconds.
- Must pull in a passerby from 10 feet in 3 seconds: poster-scale type, one idea per scene.

**Mode B: Presenter mode**
- Any input (key, click, clicker) pauses auto-advance and gives manual control. The speaker narrates; the screen shows only the words specified below.
- After 3 minutes of no input, auto-advance resumes (attract mode returns if the speaker walks away).

---

## 2. Scene-by-scene content (16 scenes, in order)

On-screen text is exact and final: a headline (max 7 words), optional support line (max 12 words), optional source credit (small, bottom left). Do not add, reword, or decorate the copy. Visual concepts are direction, not limits; keep them abstract and geometric.

| # | Headline | Support line | Credit | Visual concept |
|---|----------|--------------|--------|----------------|
| 1 | Agents worth trusting. | Your models. Your data. Your choice. | | Title card. Red Hat AI logo rises in. Generous negative space. Loop opener. |
| 2 | A billion AI agents by 2029. | Across clouds, datacenters, and edge. Are you ready? | Source: IDC, 2026 | Red dots fill six rectangular blocks like datacenters, appearing in staggered waves. Copy sits close beneath the blocks in three lines: the headline on one line at the same size as every other scene headline, the reach line smaller, "Are you ready?" in red between the two sizes. |
| 3 | Agents are everywhere, yet controls are not. | (none, single header) | | Six bounded rectangles, one per unique environment (Physical, Virtual, Private cloud, Sovereign cloud, Public cloud, Edge), each with its official Red Hat icon repository glyph centered and its name beneath. Five red dots appear and disappear in the clear space around each icon: agents existing in every environment, none governed. |
| 4 | What is an agent? | A model that plans, uses tools, and acts for you. | | One red Model node (labeled "Model") with four arms to labeled anchors: Data, Tools, Systems, Actions. Targets wander in small unsynced orbits around their anchors; red pulses travel outward (calls) and white pulses return (results) along the arms. Constant two-way activity. |
| 5 | Agents multiply inference. | Nine times the calls. Up to 70x. Every one is billed. | Source: The Cost of Dynamic Reasoning (peer-reviewed) | The official Red Hat DevOps icon with twelve small agent pulses beside it; four gray dots float through the icon in a trailing line, one behind another. |
| 6 | One door to every model. | Optimized on your hardware. Guarded on every call. | | Gateway diagram: three source pills (Users, Agents, Apps), one red Gateway bar (access, spend), two destination boxes (Self-hosted models, External models). Red dots flow through; about one in eight stops at the gate and fades. Inside Self-hosted, a GPU utilization bar fills from 30 to 80 percent. Between the two boxes, one gray text strip spanned to the exact width of the boxes: NVIDIA. AMD. Google TPUs. AWS Inferentia. Plain text only, no logos. |
| 7 | Sandbox every agent. (control word in red) | Its blast radius ends where policy draws it. | | Generated art backdrop: a glass box with one cube sealed inside. Copy in the top zone. |
| 8 | Gate models, MCPs, and agents. (Gate in red) | The agent never holds the key. The gateway does. | | Generated art backdrop (scene_gateway.png): a full-height vertical glowing gate at 58 percent of the frame, red-lit cubes low left, bright cube wall right (calmed by an edge gradient). Red dots drift through the upper corridor toward the gate; the gateway lets some pass and stops others, which fade at the line. Copy in the top zone. |
| 9 | Trace every decision. (Trace in red) | Every step recorded. Tested against attacks first. | | A timeline of dots. A red recorder dot sweeps the line; each event dot lights up as it passes and stays lit, so the record visibly accumulates, then releases. The attack node starts as a small dot; when the traveler reaches it, the node grows into the big red dot and a transparent ring is left drawn around it: the attack survived, the boundary it proved. |
| 10 | Prove before production. (Prove in red) | Benchmarks. Red teaming. Every release. | | Left: an evidence report card whose four row statuses cycle check, pending, denied, back to check, staggered and check-heavy. Right: a target that incoming arrows cannot penetrate, with a red scan line sweeping left to right, repeating. The overall impression is verified, not failing. |
| 11 | One agent, one identity. (identity in red) | No shared accounts. No anonymous agents. | | Three grayed-out shared-account cards. A red identity cursor floats across them in a loop; while it rests on a card, a check (approved) appears, occasionally swapped for an x (denied) on a white card. Approval is the norm; denial is a clear state change. |
| 12 | Sandbox. Gateway. Traceability. Proof. Identity. | Five controls. Every agent. | | The mantra scene: the five control words appear one per beat (0.3s, 1.1s, 1.9s, 2.7s, 3.5s) in Red Hat Red and drift slowly, beneath the official Red Hat DevOps loop icon with five gray agents riding its stroke in an evenly spaced train, one behind another. Five controls, one continuous cycle. The calmest scene on the screen. |
| 13 | From 10 to 1,000 agents. | One control plane. One policy for all of them. | Source: HFS Research, 2026 (82% stat below) | A density wall of exactly 1,000 dots: sixteen columns rising from a shared baseline, dots shrinking and tightening left to right until the right edge is fine grain. Columns build as groups, shimmer continuously, release, and rebuild; never static. Support stat appears small: "82% of enterprises found agents their security teams didn't know existed." |
| 14 | Agents do not keep office hours. | Your agents never stop. The platform scales with them. | | Generated art backdrop: a cube sphere with a glowing arc; red pulses breathe over the sphere and the bright cube. Copy in the top zone. |
| 15 | Same controls. Every environment. | Your cloud, your datacenter, your edge. Even air-gapped. | | One continuous Red Hat Red line across the frame, static and unbroken. Beneath it, the six environments (Physical, Virtual, Private cloud, Sovereign cloud, Public cloud, Edge), each with its official Red Hat icon repository glyph, glide slowly left in a seamless marquee, ticks and labels traveling with their icons. No vendor logos. |
| 16 | Spend less. Trust more. | Any model. Any agent. Any hardware. Across clouds. | | Closing card mirroring scene 1: logo rises in. Loop restarts here. |

Copy version note: this table is v3.1 copy with the v3.2 motion pass applied to the visual concepts. The story runs on two arcs, cost and trust: scenes 5 and 6 pose and answer the cost problem, scenes 7 to 11 answer the trust problem, and scene 16 closes both arcs in four words. The rationale for each change since v2, the one-sentence audit, and the presenter-only lines are in `2026-11-reinvent-booth-screen-copy-v3.md`.

**Motion principle (v3.1, preserved and extended by v3.2):** motion stays minimal and purposeful, one idea per scene. What changed is coverage: every scene now moves. The default is one calm, continuous animation per scene that makes the scene's single idea visible. If an animation draws attention to itself instead of to the idea, cut it or slow it down. Mechanics details and exact behaviors are in addendum sections 13 (v3.1) and 17 (v3.2, which wins where they conflict).

Notes for scenes 7 to 11: these five are the spine of the story; give them one shared visual language so they read as a family, with the number ("One:", "Two:"...) as a consistent device. They also carry a layer stack: a small vertical list at the left edge, one row per control (Sandbox, Gateway, Traceability, Proof, Identity). The current row is white with a Red Hat Red square marker, completed rows are Gray-20 with filled markers, and future rows are Gray-40 outlines. It fades in at scene 7, updates at 8, 9, 10 and 11, and hides at scene 12, where the five words take over the frame. This tells a passerby who arrived mid-sequence that there are five controls and which one is on screen.

---

## 3. Design system (Red Hat brand, exact)

**Colors (use only these):**
- Red Hat Red `#EE0000`: primary accent, key highlights, the traveling/active element
- Dark red `#A60000`: pressed/hover and darker red variant
- Deep red `#5F0000`: red shapes on the dark background
- Black `#000000`: body text on light backgrounds (unused on this dark screen, listed for completeness)
- Gray-80 `#151515`: the background for all scenes
- White `#FFFFFF`: primary text on the dark background
- Gray-40 `#A3A3A3`: source credits, secondary text
- Gray-20 `#E0E0E0`: divider lines, subtle structure

**Typography:**
- Headlines: Red Hat Display, Medium or Bold. At 1080p: 110 to 150px.
- Support lines: Red Hat Text, Regular. At 1080p: 44 to 56px.
- Source credits: Red Hat Text, Regular, 20 to 24px, Gray-40, bottom left.
- Fonts are open source (Red Hat Display, Red Hat Text). Embed as base64 woff2 from the official GitHub release (github.com/RedHatOfficial/RedHatFont). If you cannot download binaries, declare @font-face pointing to `./fonts/*.woff2` with a system-ui fallback stack, and list font embedding as the single pre-show setup step.
- Sentence case everywhere. No exclamation marks. No gradients, drop shadows, or 3D effects.

**Layout and motion:**
- Design canvas 1920x1080, scale to fit any viewport (letterbox, never crop). Keep a 5% overscan-safe margin: TVs crop edges.
- Breathing room over filling the frame; one visual element per scene plus the copy.
- Icons: consistent outline style, one stroke weight. Abstract geometry preferred over literal metaphors.
- Scene transitions: 300 to 500ms fades or subtle slides. Entrance animations inside a scene: minimal, purposeful.
- All animation via CSS/SVG. Raster images are limited to the sanctioned assets in the addendum. Prefer transform and opacity animations (GPU-cheap); nothing may make a scene feel busy from 3 meters.

---

## 4. Interaction spec

- **Next:** Space, ArrowRight, PageDown (clicker compatibility), click or tap on the right half of the screen.
- **Previous:** ArrowLeft, PageUp, click or tap on the left half.
- **Pause/resume auto-advance:** key P, or click the small pause pill (bottom right, low opacity, grows on hover-adjacent focus but must be tappable without hover).
- **Fullscreen:** F or double-tap; also attempt fullscreen on first user gesture.
- When auto-advance is paused, show a minimal "PAUSED" indicator for 2 seconds, then hide all chrome.
- **Idle rule:** 3 minutes without input in presenter mode resumes auto-advance.
- Progress: a thin row of 16 dots, bottom right, Gray-40 at low opacity; current scene dot in Red Hat Red. Hide dots during loop playback; show on any input.
- No hover-dependent functionality anywhere (booth hardware may have no cursor).

---

## 5. Technical requirements

- Single `index.html`, zero network requests at runtime (fonts embedded or local, everything inline).
- Vanilla HTML/CSS/JS only. No CDN, no imports, no analytics.
- Works in a kiosk-mode Chromium browser on a standard TV box; assume no mouse.
- The file must survive a browser reload: reload lands on scene 1 in loop mode, which is acceptable.
- No cookies, no storage requirements, no camera or microphone access.

---

## 6. Content rules (a photographed public screen)

- Never show: consumer assistant names or logos, AWS or other vendor logos, third-party agent names (Claude Code, Codex and the like stay spoken, not on screen), product screenshots, fictional UI.
- Hardware names as plain text are sanctioned in exactly one place: the silicon strip in the scene 6 gateway diagram, sitting between the two model boxes, reading "NVIDIA. AMD. Google TPUs. AWS Inferentia." No logos, no icons, Gray-40 small text. Everywhere else, prefer the generic "any accelerator."
- Every stat on screen carries its source credit exactly as given in the scene table. Do not add stats. The only on-screen numbers are: the 1 billion claim (scene 2), 9x and 70x (scene 5), the 30 to 80 percent GPU utilization bar drawn as a graphic (scene 6, no numeral), and the 82% line (scene 13). Everything else stays spoken.
- On-screen copy is dash-free: use periods, commas, colons, or parentheses; never em or en dashes.

---

## 7. Acceptance checklist (self-verify before delivering)

1. All 16 scenes present, in order, with the exact copy from the table (no rewording, no additions).
2. On-screen text contains zero em or en dashes.
3. Headlines max 7 words, support lines max 12 (scene 13's small stat line is the one sanctioned exception).
4. Zero runtime network requests (verify: open devtools, disable cache, reload, confirm no requests).
5. Loop: full run 102.4 seconds (16 scenes at 6.4s), seamless restart from scene 16 to scene 1.
6. All interactions in section 4 work, including clicker keys and the 3-minute idle resume.
7. Legibility test: at 1920x1080 viewed from 3 meters, every headline and support line is readable in 3 seconds.
8. File opens correctly with no internet connection.
9. Renders correctly at 1920x1080 and 3840x2160 without cropping scene content.
10. Scene 6: dots flow, one stops at the gate, the utilization bar animates, the silicon strip is text only.
11. Scene 15: the red line is continuous and covers all six icons; the sovereign cloud icon is the only one with a lock.
12. Motion pass: scene 3 env boxes with transient life, scene 4 two-way pulses with wandering targets, scene 8 dots passing and stopped at the gate, scene 9 record accumulates and the attack ring draws, scene 10 check-heavy cycle, scene 11 mostly approvals, scene 12 connect line draws through five nodes with the beats, scene 13 pyramid accumulates under the node, scene 15 marquee seamless under the static line, scenes 1 and 16 logo rise only.
