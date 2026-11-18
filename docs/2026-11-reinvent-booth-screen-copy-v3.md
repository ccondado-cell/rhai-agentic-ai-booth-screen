# Booth screen copy v3: rationale and audit

**Status:** FINAL. All copy locked by Carlos on Nov 16, 2026 ("I pick A" on the gateway support; "the rest I love it"; closer and opener confirmed). Updated same day by the v3.1 motion pass: scene 16 ("Reasoning is not permission.") was cut, making the final cut **16 scenes**; per-scene motion was added throughout.
**Supersedes:** `2026-11-reinvent-booth-screen-copy-v2.md` (16 scenes, different set). v3 was 17 scenes at 6.4s (108.8s); **v3.1 is 16 scenes at 6.4s: a 102.4 second loop.**

## What changed since v2, and why

1. **Coding agents scene CUT.** "Coding agents went first" was our framing, not the market's: no analyst, vendor, or leading voice attributes the agent era to coding agents. A booth screen should not carry a claim we invented. The beat it carried (agents are already in production) is now spoken by the presenter, not shown.
2. **"Almost no one governs one" merged to one header:** "Agents are everywhere, yet controls are not." Seven words, no support line. The visual does the explaining: a dense field of identical dots, none governed.
3. **"A model with hands" became a definition:** "What is an agent? / A model that plans, uses tools, and acts for you." A stranger seeing the old scene had no way to know it was a definition. The new visual (arms reaching to Data, Tools, Systems, Actions) also shows that the reach is wider than privileges, which sets up all five controls.
4. **Cost connection made explicit (scene 5):** "Nine times the calls. Up to 70x. Every one is billed." The old line left the reader to infer that calls cost money.
5. **Gateway scene ADDED (scene 6):** "One door to every model. / Optimized on your hardware. Guarded on every call." This is the answer to the cost scene, covering all three gateway ideas: access (the door), optimization (the utilization bar, 30 to 80 percent, drawn as a graphic per the Forrester TEI number), and guardrails ("Guarded", with the stopping dot showing enforcement). Metering lives in the diagram (flowing dots), not the words. Hardware names appear as plain text only (silicon strip): NVIDIA. AMD. Google TPUs. AWS Inferentia. No logos.
6. **Spine grew from four controls to five.** Proof added as control four ("Four: proof. / Benchmarks, red teaming, and evidence."), placed after the flight recorder per Carlos. We provide the tools for evaluation and red teaming; we never test agents on behalf of customers, so the copy is about tools and evidence, never a service. "Name" renamed to "Identity" (control five): with five controls the list reads as a security model, and identity is the guides' own word.
7. **"Badge" kept over "Gateway" deliberately:** scene 6's subject is the AI Gateway; if the control spine also said Gateway, the screen would have two gateways meaning two different things (platform door to models vs. agent credential to tools).
8. **Sandbox support deepened:** "Its blast radius ends where policy draws it." Containers are a commodity; the differentiator is that the boundary is policy-defined and one of five coordinated layers. OpenShell and the capabilities work stay spoken.
9. **Office hours scene reworded:** "The platform serves around the clock, worldwide." The rejected "night shift" phrasing implied agents only work while you sleep. TheBackdrop art (gen-scene13-followsun.jpg) is unchanged.
10. **Environments visual rebuilt:** one continuous red line over six outline icons (Physical, Virtual, Private cloud, Sovereign cloud, Public cloud, Edge), ported from the approved internal slide structure. No vendor logos on screen, unlike the slide.
11. **Closer:** "Spend less. Trust more. / Any model. Any agent. Any hardware. Across clouds." Four words close both arcs: spend closes the inference economics story, trust closes the controls story. Inspired by the value-framing idea, not by any vendor's words ("token" wording rejected by Carlos). The support line is approved platform language.
12. **Opener support:** "Your models. Your data. Your choice." plants the approved ownership tagline in the first three seconds and pays it off at the close. Headline stays "Agents worth trusting." because a tension stops foot traffic where a promise is wallpaper, and it is the name of the theater.

## On-screen numbers policy

Only these numbers appear on screen: 1 billion agents by 2029 (scene 2), 9x and 70x (scene 5), the 30 to 80 percent utilization bar as a graphic with no numeral (scene 6), and the 82% HFS line (scene 13). Everything else is presenter-only: 3x tokens/sec and 2x faster first token on the same hardware (llm-d), 233% ROI and 13 month payback (Forrester TEI), 60 billion tokens served weekly, MLPerf Inference v6.0 results.

## One-sentence audit (the stranger test)

| # | Scene | What a stranger gets in 3 seconds |
|---|-------|-----------------------------------|
| 1 | Agents worth trusting. / Your models. Your data. Your choice. | This is about trust, and I keep control. |
| 2 | A billion AI agents by 2029. / ...Are you ready? | Agents are coming at scale. |
| 3 | Agents are everywhere, yet controls are not. | Lots of agents, no governance. |
| 4 | What is an agent? / A model that plans, uses tools, and acts for you. | Now I know what an agent is and what it can touch. |
| 5 | Agents multiply inference. / ...Every one is billed. | Agents multiply cost. |
| 6 | One door to every model. / Optimized on your hardware. Guarded on every call. | One entry point runs models efficiently and checks every call. |
| 7 | One: a sandbox. / Its blast radius ends where policy draws it. | First control: contain the agent. |
| 8 | Two: a badge. / The agent never holds the key. The gateway does. | Second control: the platform holds credentials. |
| 9 | Three: a flight recorder. / Every step recorded. Tested against attacks first. | Third control: everything is recorded and pre-tested. |
| 10 | Four: proof. / Benchmarks, red teaming, and evidence. | Fourth control: you get evidence, not promises. |
| 11 | Five: identity. / One agent, one identity. No shared accounts. | Fifth control: every agent is identifiable. |
| 12 | Sandbox. Badge. Flight recorder. Proof. Identity. / Five controls. Every agent. | The recap: five controls, all agents. |
| 13 | From 10 to 1,000 agents. / One control plane... + 82% | It scales, and most enterprises lack this. |
| 14 | Agents do not keep office hours. / ...around the clock, worldwide. | It runs 24x7 globally. |
| 15 | Same controls. Every environment. / ...Even air-gapped. | The controls follow the work everywhere. |
| 16 | Reasoning is not permission. / The model proposes. Policy decides. | The model never gets the final say. |
| 17 | Spend less. Trust more. / Any model. Any agent. Any hardware. Across clouds. | The close: cost and trust, open, anywhere. |

## Presenter-only lines (never on screen)

- "We don't test agents for you. We give you the tools to test them yourselves: EvalHub for benchmarks, Garak results in the model catalog, adversarial testing built in."
- "Other sandboxes give you a box. This one enforces the rules you wrote, caps what it can consume, ties into identity, and records everything it did. Open source, on your infrastructure." (OpenShell and the capabilities policy stay here.)
- "The gateway also ships guardrails you can configure natively, including inline PII detection and prompt injection blocking." (The screen says "Guarded"; the mechanism stays spoken.)
- "On the same hardware, llm-d delivers 3x output tokens per second and 2x faster time to first token."
- "Forrester found 233% ROI and a 13 month payback over three years."
- "We serve 60 billion tokens a week across customers."
- "AWS reports 30 to 40 percent better price performance on Trainium2 instances versus comparable GPU instances." Attribute it to AWS; it is their benchmark, not ours.

## AWS silicon caveat (brief the booth staff)

The screen says "AWS Inferentia" as text in scene 6's silicon strip. The collaboration is public (Red Hat press release, December 2, 2025: Red Hat AI on AWS Inferentia2 and Trainium3, plus the AWS Neuron operator). However, the Red Hat AI Inference 3.5 documentation marks Trainium and Inferentia support as **Technology Preview**. If a booth visitor asks whether it is GA, the honest answer is tech preview. Do not put the 30 to 40 percent number on screen; if spoken, attribute it to AWS.

## Visual references used

- Gateway diagram structure: internal deck slide (End users / Developers / Agents → AI Gateway with access, policy controls, budget tracking → External models + Self-hosted inference → accelerated compute). Ported to the dark palette, logos removed, sources simplified to Users / Agents / Apps.
- Environments row structure: internal deck slide (six labeled environment icons under red rules). Ported with one continuous line instead of six separate rules, and no vendor logos.

## v3.1 motion pass (Nov 16, 2026)

Carlos requested more animation while preserving the minimal, purposeful principle: every scene now moves, calmly. Changes:

1. **Scene 16 cut.** "Reasoning is not permission." removed by decision. Its beat (the model never gets the final say) is carried by the sandbox support line ("where policy draws it") and the presenter track. Final count: 16 scenes, 102.4s loop.
2. **Scene 3:** transient red activation wave through the dot field. Never all red at once, or the scene would read "governed."
3. **Scene 4:** "Model" label added under the red node; targets drift unsynced; red pulses travel the arms. Communicates constant, fast, parallel activity.
4. **Scene 9:** a recorder dot sweeps the timeline; event dots light as it passes and the record accumulates.
5. **Scene 10:** row statuses cycle check, pending, denied, back to check (check-heavy); a scan line sweeps the target.
6. **Scene 11:** a red identity cursor floats across three shared-account cards, approving (check) with an occasional denial (x).
7. **Scene 12:** three unsynced marquee lines of Gray-40 supporting words (fixed vocabulary, see addendum section 13) with the five red control words between them, keeping the beat entrance.

New sanctioned on-screen text: only the scene 12 marquee vocabulary (fixed lists, no new claims). Everything else in the numbers and text policies is unchanged.

## v3.2 motion pass (Nov 16, 2026)

Carlos's ten-point refinement, all visual and layout only. Copy unchanged; the v3.1 table above remains the exact on-screen text.

1. **Scene 6:** the silicon strip moved between the two model boxes, under Self-hosted models: "your hardware" reads next to where the hardware actually sits in the diagram.
2. **Scene 13:** the agent grid now grows in with a staggered sweep, holds, and resets. The population visibly builds under the one policy ceiling.
3. **Scene 15:** the six environments became a slow seamless marquee under the static red line. The line is the control; the environments keep passing beneath it: same controls, every environment, endlessly.
4. **Scene 2:** the random dot burst became concentric spawn rings, each larger and denser than the last. Growth you can see accelerate, matching "a billion by 2029."
5. **Scene 4:** targets wander in small unsynced orbits, and traffic now runs both ways: red pulses out (calls), white pulses back (results). The agent is in conversation with its world, not just reaching at it.
6. **Scenes 7, 8, 14:** the generated JPEGs get overlay motion (red pulse contained in the glass box, a glow traveling the gate line, pulses breathing on the sphere). Three full options were prepared for scenes 7 and 8 (overlay on existing art, new animatable art via generation prompts, flat SVG); option A is implemented, B and C are in `banana-playbook.md` for assessment.
7. **Scene 9:** the attack moment. When the recorder reaches the attack node it turns white inside it, the chevron above fades, and a ring is left drawn around the node: the test leaves a visible boundary behind.
8. **Scene 12 (designer's choice):** the marquee was cut. The five control words keep their beat entrances, and a thin red line now draws itself through five nodes, one per beat. My call, and the reasoning: the marquee was the busiest scene on the screen and the only one whose motion was decoration rather than meaning. You asked whether words connecting everything together would beat scrolling words; they do. The scene is now the calmest on the screen, which is where a recap belongs. The marquee vocabulary is therefore no longer sanctioned on-screen text.
9. **Scenes 1 and 16:** the logo now rises in and a thin red line sweeps once down the card. Slightly stronger motion on the two cards a passerby sees first and last, with the copy still landing first.

## v3.3 scene pass (Nov 16, 2026)

Carlos's five-point refinement after reviewing v3.2, all visual only. Copy unchanged.

1. **Scenes 1 and 16:** the red sweep is gone. The logo rise carries both cards alone; calmer, as the sweep was motion without meaning.
2. **Scene 2:** agents are now organized into six datacenter-like blocks that fill most of the space above the headline, dots appearing in staggered waves. "A billion" now reads as structured scale, not scattered growth. (Carlos picked the blocks reading.)
3. **Scene 3:** the bare dot field became eight bounded environment rectangles, each holding one icon from the scene 15 family, with red dots appearing and disappearing inside. The ungoverned story now shows *where* agents live: everywhere, in every shape of environment.
4. **Scene 8:** the overlay was rebuilt as gate traffic: many dots drifting toward the gate; the gateway lets some pass and stops others at the line. Bonus fix: a pixel-brightness measurement of the actual JPEG showed the gate is a vertical line at mid-frame, so the dots travel horizontally through it; the v3.2 horizontal traveler had been misaligned.
5. **Scene 13:** dots and ceiling line replaced by a control-plane pyramid: agent dots accumulate under one red node, each tethered by a thin line. Growth shown structurally, so no new numerals on screen. (Carlos confirmed full replacement.)

## v3.4 scene pass (Nov 16, 2026)

Carlos's ten-point refinement after reviewing v3.3: six build changes (below) plus four research deliverables (in `reinvent-booth-screen/2026-11-reinvent-booth-screen-v3.4-research.md`, recommendations only, no screen change without approval).

1. **Scene 3:** icons now sit at the center of each environment box with their names beneath (exact scene 15 labels), and five larger red dots (r 5.5) appear and disappear in the clear space around each icon, never on top of it. The life is now impossible to miss.
2. **Scene 2:** three-line treatment, same words: the headline largest and on one line, "Across clouds, datacenters, and edge." smaller, and "Are you ready?" in red, sized between the two so the challenge lands.
3. **Scene 9:** the V is gone. The attack node starts as a small dot and grows into the big red dot as the recorder arrives, with the white ring left drawn around it: the moment is now the growth itself.
4. **Scene 11:** the X swaps in place of the check (no overlap) and the cursor's rectangle turns white while the denial shows. Denial is a state change, not a double exposure.
5. **Scene 12:** the connect line became an infinity loop, the DevOps convention: the loop draws itself, one node lands per beat, and small agents flow continuously through it. Five controls, one continuous cycle.
6. **Scene 13:** the pyramid became a growing chart: ten even dot columns rising from a flat baseline, building left to right, no taper. Structured growth again.

## v3.4.1 copy decisions (Nov 16, 2026)

 Carlos approved the B1 and B3 recommendations from the v3.4 research. **The copy table above is now superseded in four places:**

1. **"Badge" → "Gateway"** everywhere: scene 8 headline is now "Two: a gateway." (support unchanged: "The agent never holds the key. The gateway does."), the layer stack row reads Gateway, and the mantra beat word is Gateway.
2. **"Flight recorder" → "Traceability"** everywhere: scene 9 headline is now "Three: traceability." (support unchanged), the layer stack row reads Traceability, and the mantra beat word is Traceability.
3. **The five controls are now: Sandbox. Gateway. Traceability. Proof. Identity.**
4. **Scene 14 support line** is now "Your agents never stop. The platform scales with them." (headline unchanged), carrying the intent that the platform keeps up with nonstop agents rather than merely being available.

Rationale for both word choices is in `reinvent-booth-screen/2026-11-reinvent-booth-screen-v3.4-research.md` (B1 and B3). On-screen word-count limits are respected. The v3.1 table above remains as the historical record of the locked pre-swap copy.

## v3.5 polish pass (Nov 16, 2026)

Seven-point visual review from Carlos, plus the pre-approved adoption of his generated gate image for scene 8. **No copy changed in this pass**; every word on screen is exactly as locked in v3.4.1. Build details are in `reinvent-booth-screen/addendum.md` section 20. In short:

1. Scene headlines harmonized: all scene headers one step smaller, scene 2's headline raised to the same size, and scene 2's copy moved up against the datacenter blocks.
2. Scene 3 now shows exactly six unique environments (no repeats) with official Red Hat icon repository glyphs, labels clear of icons.
3. Scene 6's silicon strip is spanned to the exact width of the model boxes, with the boxes spaced further apart.
4. Scene 11's denial X is near-black on the white rectangle.
5. Scene 5 uses the repository's DevOps icon with four gray agents trailing through it.
6. Scene 13 is now a density wall of exactly 1,000 dots that never stops moving (columns build, shimmer, release, rebuild); the red control-plane dot is gone.
7. Scene 15's marquee uses the same repository icons.
8. Scene 8 adopts Carlos's scene_gateway.png, with the gate traffic retuned to the measured gate position and red dots kept (his "Keep the Dots" call).

## v3.6 copy pass (Nov 16, 2026): value-based spine headlines

Carlos approved replacing the ordinal spine headlines ("One: a sandbox." ... "Five: identity.") with verb-led value lines, each carrying its control word in Red Hat Red inside the headline (echoing the red beat words and layer stack). The layer stack and mantra keep the locked nouns: Sandbox, Gateway, Traceability, Proof, Identity.

| Scene | Old headline | New headline | Support |
|---|---|---|---|
| 7 | One: a sandbox. | **Sandbox** every agent. | unchanged |
| 8 | Two: a gateway. | **Gate** models, MCPs, and agents. | unchanged: The agent never holds the key. The gateway does. |
| 9 | Three: traceability. | **Trace** every decision. | unchanged |
| 10 | Four: proof. | **Prove** before production. | Benchmarks. Red teaming. Every release. |
| 11 | Five: identity. | One agent, one **identity**. | No shared accounts. No anonymous agents. |

Rationale: scenes 7 to 9 share one cadence (verb, object, scope) so the five controls read as one system; the breadth of Red Hat's gateway (keys, models, MCPs, agents) is split between scene 8's headline (what passes through) and support (who holds the key), which is the differentiator against commodity AI gateways. Scene 10's support trades "evidence" (now redundant with "Prove") for "Every release," adding the continuous-proof dimension. Scene 11 promotes the strongest existing identity line to the headline; the new support calls back to scene 3's ungoverned agents. Word-count limits respected: longest headline 5 words, longest support 6.

## v3.7 copy pass (Nov 18, 2026): field-feedback support swaps

Field feedback on two support lines; headlines untouched. Both swaps were screened against the Red Hat brand voice (plain cause-and-effect, no security-team jargon) and Carlos converged on the final wording from the screened option set. Word-count limits respected (8 and 6 words; limit 12; no em or en dashes). No other copy changed; the v3.6 spine headlines stand.

| Scene | Old support | New support | Rationale |
|---|---|---|---|
| 7 | Its blast radius ends where policy draws it. | If an agent misbehaves, it goes nowhere else. | "Blast radius" reads as security-team jargon at a 3-second booth glance; the line keeps the same containment promise (a misbehaving agent is bounded by the sandbox) in plain cause-and-effect. The policy-drawn-boundary nuance from the v3.4 rationale above remains the design intent; the on-screen line now carries it implicitly. |
| 9 | Every step recorded. Tested against attacks first. | Every step recorded. Tested against attacks. | "First" asserted a timing claim that is unclear at a glance; the pre-production sequencing is already owned by scene 10 ("Prove before production"). |
