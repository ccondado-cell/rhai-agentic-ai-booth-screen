# Addendum: implementation decisions and asset manifest

This addendum is part of the brief above. The section numbering continues from it.

**Two clarifications that supersede the brief where they conflict:**
1. Section 3 says raster images are limited to sanctioned assets. The official logo and the 3D brand assets listed below are exactly those sanctioned exceptions.
2. Scenes 1 and 16 do not repeat "Red Hat AI" as support text, because the logo image already carries the wordmark. The headline stands alone on both cards.

## 8. Asset manifest (already downloaded and in the project folder)

All files are local. Reference them exactly as listed. Do not invent filenames. Do not fetch anything from the internet.

**Logo (scenes 1 and 16):**
- `assets/red-hat-ai-logo-reverse.png` (white "Red Hat AI" wordmark, transparent, made for dark backgrounds)

**3D icons (all spares, none referenced since v3):**
- `assets/3Dobj-RH_AI_tech_icon-R_5K_300dpi.Large_square_transparent.png`
- `assets/3Dobj-RH_AI_tech_icon-L_5K_300dpi.Large_square_transparent.png`
- `assets/3Dobj-RH_AI_tech_icon-S_5K_300dpi.Large_square_transparent.png`

**3D scene illustrations (1920x1080, transparent, dark purple cube imagery):**
- `assets/3Dtex-AI-BG-01-ToT_dark.FullHD_transparent.png` (low cube skyline with empty sky; backdrop for scenes 1 and 16, opacity 0.45)
- `assets/3Dtex-AI-Hero-02-ToT_dark.FullHD_transparent.png` (dome world of cubes; backdrop for scene 2, opacity 0.28)
- `assets/3Dtex-AI-CU-02-ToT_dark.FullHD_transparent.png` (close-up cube field with pieces breaking away; backdrop for scene 3, opacity 0.22)
- `assets/3Dtex-AI-Hero-01-Tot_dark.FullHD_transparent.png` (wall of cubes; backdrop for scene 13, opacity 0.22)
- `assets/3Dtex-AI-BG-02_Dark.FullHD_transparent.png` (spare, not used)
- `assets/3Dtex-AI-CU-01-ToT_dark.FullHD_transparent.png` (spare, not used)

**Fonts (already downloaded, reference via @font-face):**
- `fonts/RedHatDisplay-Medium.woff2` (weight 500)
- `fonts/RedHatDisplay-Bold.woff2` (weight 700)
- `fonts/RedHatText-Regular.woff2` (weight 400)

**Generated art (created with an image model, already selected and in place):**
- `assets/gen/gen-scene07-sandbox.jpg` (2752x1536, pure black background, a glass box with one cube sealed inside; full-bleed backdrop for scene 7 at opacity .75)
- `assets/gen/scene_gateway.png` (2752x1536, near-black background, a full-height glowing gate column measured at x 58.4 percent, red-lit cube cluster low left, bright lavender cube wall on the right; full-bleed backdrop for scene 8 at opacity .85 with a right-edge darkening gradient. Adopted in v3.5, Carlos generated it with Gemini)
- `assets/gen/gen-scene08-badge.jpg` (retired in v3.5, kept as spare; was scene 8's backdrop before scene_gateway.png)
- `assets/gen/gen-scene13-followsun.jpg` (2752x1536, pure black background, a cube sphere with a glowing arc and one bright cube on it; full-bleed backdrop for **scene 14** at opacity .7. The filename says scene13 for historical reasons; it is referenced by scene 14.)

**Red Hat icon repository glyphs (360x360 PNG, Red Hat Red on transparency, from the official Red Hat Icon Repository; copied from the redhat-slides skill's extracted set, referenced by scenes 3, 5 and 15):**
- `assets/icons/app-on-server-176.png` (Physical)
- `assets/icons/virtual-server-stack-144.png` (Virtual)
- `assets/icons/cloud-private-198.png` (Private cloud)
- `assets/icons/sovereign-cloudnew-244.png` (Sovereign cloud)
- `assets/icons/cloud-178.png` (Public cloud)
- `assets/icons/edge-204.png` (Edge)
- `assets/icons/devops-586.png` (DevOps loop, scene 5)

These three are JPEGs with no transparency; they are designed to be shown full-bleed over the `#151515` background. Because they carry their own black background, do not apply blend modes. Keep the `.text-block` scrim (radial gradient from `rgba(21,21,21,0.92)` to transparent) so white type always reads over them. Spare candidates live in `assets/gen/alternates/`; do not reference them.

**Important about the 3D illustrations:** they are official Red Hat AI brand assets with a purple/lavender glow. That purple is part of the official AI 3D visual language and is allowed inside these images only. All interface accents you create (dots, pulses, arrows, highlights) stay Red Hat Red `#EE0000`.

## 9. Implementation decisions already validated

These were found and fixed in a prior build. Treat them as requirements, not suggestions.

1. **Loop timing:** 6400 ms per scene. 16 scenes, so the full loop is 102.4 seconds. Restart seamlessly from scene 16 to scene 1.
2. **Keyboard mapping, in this exact order of handling:**
   - P toggles pause/resume directly. It must work while the loop is running (do not route P through an "any input pauses the loop" branch, or it will pause and immediately un-pause).
   - F toggles fullscreen and must not pause the loop.
   - Space, ArrowRight, PageDown advance; ArrowLeft, PageUp go back.
   - Space must call preventDefault.
   - Any other input pauses auto-advance and starts the 3 minute idle timer.
3. **Generated repeated elements use `innerHTML` inside the main init script, never `document.write`:** scene 2's swarm dots, scene 3's agent field (24 outlined circles, 8 by 3, staggered wave delays), scene 5's twelve small pulses, scene 6's gateway dots, scene 9's recorder dots, scene 10's report rows, scene 11's identity cards, scene 12's marquee tracks, scene 13's dot grid.
4. **Scene 6 gateway, exact behavior:**
   - The utilization bar (`#gw-util-fill`) animates with a CSS `scaleX` transform from 0.375 to 1 (30 to 80 percent), `transform-box: fill-box`, `transform-origin: left center`, 3.2s ease-in-out infinite alternate.
   - Five dot streams (three inbound from Users, Agents, Apps; two outbound to the model boxes), three dots each, 2.4s loops, staggered delays, using `translate(var(--dx), var(--dy))` keyframes.
   - Two stopping dots travel to the gate, hold, and fade in place over 4.8s: the visual form of "Guarded on every call." Keep the fade subtle; never a red X.
   - The silicon strip ("NVIDIA. AMD. Google TPUs. AWS Inferentia.", plain Gray-40 text, no logos) sits between the two model boxes: directly under the Self-hosted models box, above the External models box. (Moved there by v3.2; see section 17.1.)
5. **First-gesture fullscreen:** a once-only click listener that requests fullscreen. Double tap on touch also toggles. F toggles.
6. **Scene 12 (mantra):** the five control words appear at 0.3s, 1.1s, 1.9s, 2.7s, 3.5s after the scene becomes active, drifting slowly (9s ease-in-out alternate, 14px each way). Reset the word animations when the scene re-enters (scene array index 11) so the beats replay on every loop pass. The marquee lines run continuously and are not reset.
7. **Backdrops:** position absolute, inset 0, z-index 0, `object-fit: cover`; content wrapper z-index 2; credits above. Each active scene's backdrop runs a 7 second scale drift from 1 to 1.07.
8. **Layout:** body overflow hidden; each scene has 5% padding on all sides for overscan; content is a flex column with the visual above and the text block below, centered.
9. **Progress dots:** 16 dots, bottom right at 5% inset, hidden during loop playback, shown as soon as a presenter takes control. Current dot in Red Hat Red, the rest Gray-40 at low opacity.
10. **Pause pill:** bottom right, low opacity until hover-adjacent, tappable, shows a play glyph when paused and a pause glyph when running.
11. **Scene copy is final.** Copy it exactly from the table in brief section 2. Do not reword, shorten, or add words. The only sanctioned extra text is scene 13's 82% line, the source credits, scene 6's silicon strip, and scene 12's marquee vocabulary (the fixed word lists in section 13).
12. **Layer stack on scenes 7 to 11.** A fixed element, absolutely positioned at left 4 percent and vertically centered, listing five rows: Sandbox, Badge, Flight recorder, Proof, Identity. One row per control, 18px square marker plus label, Red Hat Text at about 26px. Current row: white label, Red Hat Red filled marker. Completed rows: Gray-20 label and filled marker. Future rows: Gray-40 label and outline marker. It fades in on scene 7, updates on 8, 9, 10 and 11, and fades out on scene 12 and every other scene. It must be pointer-events none and must not overlap the scene's own illustration.
13. **On-screen copy is the v3.1 table.** The brief's section 2 table is v3.1. Use it exactly. Presenter-only lines from v1 and v2 are deliberately not on screen.
14. **Generated-art scenes place copy in the top zone.** Scenes 7, 8 and 14 carry the class `text-top` as well as `scene`. For those three, the content wrapper justifies to the top (`justify-content: flex-start`) and the text block's min height drops to 20vh, so the headline sits in the deliberately empty upper part of the image and the artwork fills the lower half. The measured white-text contrast in that top band is 14:1 or better. Do not center the copy vertically on these three scenes: the artwork is centred low and the type would land on top of it.
15. **Scene 15 environments, exact behavior:** one continuous Red Hat Red line (stroke width 4) runs the full width, unbroken. Seven ticks (stroke width 3) drop from the line to the six icons. Icon order left to right: Physical (server rack), Virtual (two overlapping rounded rects), Private cloud (plain cloud outline), Sovereign cloud (cloud plus a small padlock, the only deviation), Public cloud (cloud with up and down arrows inside), Edge (hub with four spokes). Labels beneath in Gray-40 at about 19px. No vendor logos anywhere in this scene.
16. **Scene 3 is a single header with no support line.** The visual carries the meaning: a dense uniform field of identical outlined circles, all equal, none marked. The red activation wave is transient and partial (see section 13); never fill all dots red at once, or the scene reads "governed."

## 13. Motion pass v3.1 (superseded in places by section 17, v3.2)

The design principle is unchanged: motion is minimal and purposeful, one idea per scene, and every animation must earn its place at a 3-second glance. What changed is coverage: every scene now moves. The default is one calm, continuous animation per scene that makes the scene's single idea visible. If an animation draws attention to itself instead of to the idea, cut it or slow it down. Mechanics are implemented as specified below; be creative only within these bounds. When choosing between a richer effect and a calmer one that communicates the same idea, take the calmer one.

**Scene 3, activation wave:** each of the 24 field dots runs a 6s `field-wave` keyframe (transparent fill, brief red fill at 10 percent, back to transparent by 26 percent), delayed by `(row * 8 + column) * 0.18s`, so a slow red wave crosses the grid and the field rests quiet before it repeats. Transient and partial by construction.

**Scene 4, constant reach:** the four target groups (circle plus label) run `reach-float`, a 3.6s ease-in-out alternate vertical drift of 6px, delayed 0s, 0.9s, 1.8s, 2.7s so they are never synced. Four red `arm-pulse` dots (r 5) travel from the model node outward along the arm vectors (`--dx`/`--dy`: 235px, 88px in the four sign combinations) on the shared `gw-flow` keyframes at 2.8s, delayed 0s, 0.7s, 1.4s, 2.1s. The label "Model" (Gray-20, 20px) sits under the red node. Labels never travel; only the nodes drift.

**Scene 9, the record accumulates:** a red traveler dot (r 9) runs `rec-run`: 4s linear, translateX 0 to 400px along the line, fading in at the start and out at the end. Five event dots (x 100, 150, 200, 250, 380; r 8) run `rec-pass` on the same 4s cycle, each delayed by `(x - 50) / 400 * 4` seconds, so each dot turns red exactly as the traveler passes, holds red for most of the cycle (the record grows), then releases and resets when the traveler restarts.

**Scene 10, continuous assessment:** four report rows (y 92, 126, 160, 194; line x 30 to 140, Gray-40) each carry three stacked status glyphs with 4.8s cycles: a red check polyline, a Gray-20 pending dot, a Gray-40 x, staggered by row delay of i * 0.9s with `animation-fill-mode: backwards` (so all rows start as checks and cycle out of phase). Timeline per cycle: check 0 to 48 percent, pending 54 to 62, x 72 to 80, back to check by 98. The impression is verified, never failing. On the target, a red vertical scan line (stroke 3, y 58 to 182, starting at x 36) runs `proof-sweep`: 3s ease-in-out, translateX 0 to 128px with opacity fading in and out at the ends. The two static red arrows remain: attacks stopped at the boundary.

**Scene 11, the identity cursor:** three grayed-out account cards (x 80, 170, 260; 60 by 90, person glyph inside, generated by JS). A red cursor group (66 by 98 rounded rect, red stroke, translucent red fill, base position over the middle card) runs `id-float` on a 6s cycle: middle (0 to 22 percent), left at -90px (30 to 47), right at +90px (55 to 72), middle (80 to 100). Inside the cursor, a red check polyline is visible whenever the cursor rests on a card, and a Gray-20 x appears only during 87 to 92 percent (one denial per cycle, at the middle position). Approval is the norm; denial is the feature.

**Scene 12, the mantra marquee (REPLACED by v3.2, see section 17.8):** this scene was rebuilt as the connect-line design. The marquee description below is retained only for history; do not implement it. Each `.marquee` clips an inline-flex track of Gray-40 words (Red Hat Text, clamp 20 to 30px, 0.75 opacity, 2.5em gaps) with the word list repeated twice for a seamless loop. Line 1 scrolls left (translateX -50 percent to 0, 26s), line 2 scrolls right (0 to -50 percent, 21s), line 3 scrolls left slower (33s). The three speeds guarantee desync. The five control words keep their beat entrance (0.3s, 1.1s, 1.9s, 2.7s, 3.5s) and the whole h1 drifts 14px left and right over 9s, alternate. Fixed word lists (no new claims):
- Line 1: Identity. Governance. Trust. Isolation. Containment. Limits. Attribution.
- Line 2: Control. Tracing. Credentials. Keys. Access. Records. Audit. Visibility.
- Line 3: Evidence. Badge. Benchmarks. Testing. Red teaming. Validation. Provenance. Policy.

**Global motion constraints:** CSS/SVG only, transform and opacity preferred (GPU-cheap for kiosk hardware), no JS animation libraries, no SMIL, nothing may make a scene feel busy from 3 meters, and all section 9 rules still apply.

## 14. Freedom you have (and freedom you do not have)

You may redesign the inline SVG illustrations for scenes 4, 6, 9, 10, 11, 13 and 15 if you have a stronger idea, as long as you keep one idea per scene, use only the palette in section 3, keep outline iconography consistent, keep the five-scene spine (7 to 11) reading as a family with the "One:", "Two:", "Three:", "Four:", "Five:" device, and keep the motion behaviors in section 13 (their goals are fixed; only equivalent mechanics may be swapped).

You may not change: the scene order, the on-screen copy, the interaction map, the timing, the brand tokens, or the file structure (one HTML file, local assets, no network).

## 15. Self-check before you answer

1. 16 scenes, exact copy, zero em or en dashes on screen.
2. All asset paths match section 8 exactly, and every referenced file exists in the folder.
3. Zero runtime network requests.
4. Loop total is 102.4 seconds and returns to scene 1 cleanly.
5. P, F, Space, arrows, PageUp/PageDown, click zones, double tap, idle resume all work.
6. No `document.write`.
7. Scene 6 dots flow and one stops at the gate; scene 15's red line covers all six icons; scene 12 replays its five beats on re-entry while the marquee runs continuously.
8. Motion pass verified: scene 3 wave transient, scene 9 record accumulates, scene 10 check-heavy, scene 11 mostly approvals, scene 12 lines unsynced.
9. Headline and support text readable in 3 seconds at 3 meters on a 1920x1080 screen.
10. HTML parses with no unclosed tags.

## 16. Visual DNA of the 3D assets (for any new art you generate)

You cannot see the image files, only these rules. If you create new decorative art, match this description rather than inventing a style. Prefer SVG and CSS over raster output: you cannot generate PNG or GIF files, and SVG stays crisp at 4K.

**Subject:** a "data terrain" built from many small rounded-corner cubes, rendered in 3D with a soft studio look.

**Palette and light:**
- Cube base: near-black with a faint purple tint, roughly `#0B0B0D` to `#1A1A1E`.
- Glow: sparse lavender faces acting as light sources, roughly `#B07CF0` to `#D9C4FF`. About one cube in forty glows. Scarcity is the effect; do not blanket the scene.
- Occasional single red cube `#EE0000` is permitted as an accent, matching the BG-02 asset.
- No other hues.

**Surface:** glossy, glass-like cubes with soft reflections and visible ambient occlusion in the gaps. Slight depth of field on close-up compositions.

**Composition:**
- Background variants: low horizon, wide empty sky above, the terrain anchored to the bottom edge.
- Close-up variants: diagonal grid of cubes converging toward a vanishing point, some cubes breaking loose and floating away.
- Hero variants: one massive object (a dome or tower) isolated against empty space.

**Do not add:** text, logos, people, stars, glows or flares outside the cube faces, hard gradients, or any color not listed above. Backgrounds are transparent, 16:9.

**If you need motion:** animate with CSS transforms (slow scale drift, drifting particles, pulsing glow). Never emit a GIF or video reference.

## 17. Motion pass v3.2 (Nov 16, 2026; wins over section 13 where they conflict)

Ten changes requested by Carlos. All are visual and layout only: every headline, support line, credit and claim stays exactly as written. The calm-motion rule is preserved. Implemented as option A for scenes 7/8 (overlay motion on the approved JPEGs); option B generation prompts and option C SVG concepts live in `banana-playbook.md` for assessment.

1. **Scene 6 (17.1):** silicon strip moved into the SVG between the two model boxes (x 760, y 175, 14px Gray-40). Same four names, plain text.
2. **Scene 13 (17.2):** the 80 grid dots now grow in with a staggered sweep (`grid-grow`, 12.8s cycle, ~2.2s stagger, per-dot opacity variance), hold, and reset: the population visibly grows under the one policy ceiling.
3. **Scene 15 (17.3):** the six icon-plus-tick-plus-label groups are one `env-set` group rendered twice (`<use>` at x 0 and 960) inside an `env-track` translating -960px to 0 over 36s linear: a seamless left-to-right marquee. The red line is static and drawn last on top.
4. **Scene 2 (17.4):** the random burst is replaced by concentric spawn rings (`spawn-dot`/`spawn`, 10s cycle): six rings, radius 18 to 88px, 6 to 20 dots each, slightly larger dots outward, ring delay k * 0.6s. Agents multiplying outward from a point, accelerating. IDC credit unchanged.
5. **Scene 4 (17.5):** the four targets now wander (`reach-orbit`, small 8px circular paths, durations 7 to 11s, negative delays so they are never synced; labels travel with their groups). Arms stay static to the anchors. Red pulses (r 5) run model-to-target as before; four new Gray-20 return pulses (r 4) run target-to-model: calls out, results back.
6. **Scenes 7, 8, 14 (17.6, 17.9):** `overlay-art` layers over the JPEGs. Scene 7: one red `art-pulse` (24vmin) swelling inside the glass box at 50%/60%. Scene 8: an `art-traveler` glow crossing the gate line left to right (6s, top 56%) plus a smaller pulse at 32%/58%. Scene 14: two pulses (16vmin at 50%/38%, 8vmin at 63%/47%, offset by 2s). Overlay positions are approximations against the JPEG compositions and must be eye-checked; JPEG pixels cannot move, only the overlays.
7. **Scene 9 (17.7):** the attack moment. The red chevron (`.attack-v`) fades out at 66% of the 4s traveler cycle and is replaced by `.attack-ring`, a transparent circle (r 24, Gray-20 stroke) scaling in around the red node from 69%. The traveler's fill turns white from 65% to 76% while inside the node (rec-run keyframes), back to red as it exits. The ring persists to 88%, then everything resets: the test leaves a visible boundary behind.
8. **Scene 12 (17.8, designer's choice):** the marquee is gone. Option ii implemented: the five beat words keep their entrances (0.3s to 3.5s, 9s drift), and above them a thin red `connect-line` (pathLength 100, dashoffset draw over 3.4s from 0.3s) runs through five `connect-node` circles (cx 40 + i * 140, r 7, popping in at 0.3s + i * 0.8s, matching each beat). The recap literally connects everything together, and the scene is now the calmest on the screen. Rationale: Carlos asked whether words that connect everything would beat the marquee; the marquee was the busiest scene on the screen and the only one whose motion was decoration rather than meaning. Re-entry restart now covers `.beat-word, .connect-line, .connect-node` at index 11.
9. **Scenes 1 and 16 (17.10):** the logo rises in (`logo-in`, 1.4s, 22px rise from 0.2s) and a thin red `card-sweep` line travels top to bottom over the scene's 6.4s (fades out at the end, no loop): a slightly stronger sense of motion with the copy still landing first. Restarted on re-entry at indices 0 and TOTAL_SCENES - 1.

**Marquee vocabulary note:** with scene 12's marquee gone, the fixed word lists from section 13 are no longer sanctioned on-screen text anywhere. The only sanctioned extra text remains scene 13's 82% line, the source credits, and scene 6's silicon strip.

**Option B and C for scenes 7 and 8** (generation prompts and SVG concepts, for assessment only, not implemented) are in `banana-playbook.md`.

## 18. Motion pass v3.3 (Nov 16, 2026; wins over sections 13 and 17 where they conflict)

Five changes requested by Carlos after reviewing v3.2 in code. Copy unchanged. The v3.2 items superseded here: 17.4 (scene 2 spawn rings), the scene 8 part of 17.6 (traveler + pulse), 17.2 (scene 13 grid growth), and the `card-sweep` part of 17.10. Gate geometry below was measured from the actual JPEG with a pixel-brightness profile, not eyeballed.

1. **Scenes 1 and 16 (18.1):** the red card sweep is deleted (element, CSS, keyframes, and its restart branch). The logo rise-in is the only motion on both cards.
2. **Scene 2 (18.2):** dots organized in datacenter blocks. Six rectangles (260x140, three by two, thin Gray-40 outlines at 0.45 opacity) in an 880x340 SVG; each block holds a 10x6 grid of red dots (r 3.5). Dots appear in staggered waves (`dc-grow`, 11s cycle, block delay b * 0.7s plus intra-block stagger), hold, and reset: structured capacity building up. The visual container is raised to 56vh so the blocks use the majority of the space above the headline. Carlos confirmed the "blocks like datacenters" reading.
3. **Scene 3 (18.3):** the 8x3 dot field is replaced by eight environment rectangles (172x110, four by two), each containing one icon from the scene 15 family (Physical, Virtual, Private cloud, Sovereign cloud, Public cloud, Edge, repeated once). No labels: the icons are taught in scene 15. Inside each box, three small red dots (`env-life`, 4.5 to 7.7s cycles, staggered delays and durations) appear and disappear transiently: agents existing inside every environment, none governed. The field-wave CSS is removed.
4. **Scene 8 (18.4):** gate traffic. The gate in gen-scene08-badge.jpg is a vertical luminous line measured at x 49 to 50 percent (spanning y 32 to 94), so dots travel horizontally: nine red dots (`gate-dot`, tops spread 38 to 71 percent), six `pass` (drift from 6 percent left, through the gate at 49.5, continue and fade by 74 percent) and three `stop` (halt at 49 percent and fade in place, never a red X). Durations 6 to 8.4s, delays staggered 0.9s. The v3.2 traveler and pulse overlay is removed; the old horizontal traveler was misaligned with the real vertical gate anyway.
5. **Scene 13 (18.5):** the dot grid and ceiling line are replaced by one control-plane visualization: a red node (r 14, plus a faint ring) at the top, with 42 Gray-20 dots accumulating beneath it in a widening pyramid (rows of 3 to 9), each tethered to the node by a thin Gray-40 line. Dots and lines appear in order (`ctrl-grow`, 12.8s cycle, delay idx * 0.16s, ~6.7s build), hold, and churn calmly. No new numerals: the growth is shown structurally, keeping the on-screen numbers policy intact. Carlos confirmed full replacement over the v3.2 grid growth.

Also in this pass: the scene 7 pulse moved to the measured box-glow center (50% / 63%) and the scene 14 pulses to the measured sphere center (50% / 45% and 61% / 50%).

## 19. Scene pass v3.4 (Nov 16, 2026; wins over sections 13, 17 and 18 where they conflict)

Six build changes from Carlos's review of v3.3, all visual/layout except scene 2's typographic treatment (wording unchanged). Research deliverables from the same pass (word-swap candidates, Gemini image route, scene 14 line, agent-definition check) are in `2026-11-reinvent-booth-screen-v3.4-research.md` and change nothing on screen until Carlos approves.

1. **Scene 3 (19.1):** each environment rectangle (now 172x130) carries its icon at the vertical center and its name beneath it in Gray-40 16px (exact scene 15 labels). Five transient red dots (r 5.5, up from 3) sit in fixed clear-space spots around the icon and label, never on top of either, with staggered durations (4.5 to 7.7s) and delays. Dot spots are box-local corners and edges.
2. **Scene 2 (19.2):** three-line treatment, wording unchanged. Line 1 "A billion AI agents by 2029." on one line at clamp(48px, 5.6vw, 108px) with nowrap (down from the 8vw default so "Are you ready?" can breathe). Line 2 "Across clouds, datacenters, and edge." at clamp(24px, 2.4vw, 44px). Line 3 "Are you ready?" in Red Hat Red, Bold, at clamp(34px, 3.6vw, 72px): larger than line 2, smaller than line 1.
3. **Scene 9 (19.3):** the V chevron is deleted. The attack node is a red circle (r 16) that starts at scale 0.5 (reads as a small dot) and grows to full size as the traveler arrives at 65 percent of the 4s cycle (`attack-node` keyframes, transform-box fill-box), while the white ring draws in as in v3.2. The traveler still turns white inside the node from 65 to 76 percent; if that double-reads on screen, drop the white fill and let the growth carry the moment.
4. **Scene 11 (19.4):** the X now replaces the check instead of overlapping: check visible 0 to 82 and 98 to 100 percent, X visible 86 to 94 percent, and the cursor rectangle's fill animates from translucent red to white (rgba 255,255,255,0.92) exactly while the X shows (`id-rect` keyframes on the rect, inline fill kept as fallback). Denial reads as a state change.
5. **Scene 12 (19.5, creative freedom):** implemented as the infinity loop (option ii): the straight connect line is replaced by a lemniscate path (M320,40 C280,12 140,12 100,40 ... Z, Red Hat Red stroke 2) that draws itself as before, five red nodes land on the loop per beat (left edge, left-top, center crossing, right-top, right edge), and two small Gray-20 agents flow continuously through the loop via CSS `offset-path` (7s, staggered 3.5s). Rationale: the DevOps infinity convention reads instantly as "continuous cycle," it keeps all five controls connected, and the slow gray flow is calmer than any pulse option. Re-entry restart still covers the line and nodes; the flow dots run continuously.
6. **Scene 13 (19.6):** the pyramid is replaced by a dot-column chart growing left to right: ten evenly spaced columns (x 88 + c * 52), column c has c + 1 dots (1 to 10) stacked upward from a common baseline (y 258, gap 18, r 5, Gray-20). Columns build left to right (delay c * 0.5s plus intra-column 0.06s) on the 12.8s cycle, hold, and churn. Flat baseline, no taper. The control-plane node stays above the chart; the tether lines are omitted so the chart reads clean. No new numerals.

### 19.7 Copy decisions applied (v3.4.1, Carlos approved the research recommendations)

- **Badge → Gateway, Flight recorder → Traceability, everywhere:** scene 8 headline "Two: a gateway.", scene 9 headline "Three: traceability.", layer stack rows Gateway and Traceability, mantra beat words Gateway and Traceability. The five controls are Sandbox, Gateway, Traceability, Proof, Identity. Scene 8's support line ("The agent never holds the key. The gateway does.") now names the control directly.
- **Scene 14 support line → "Your agents never stop. The platform scales with them."** (headline unchanged).
- Rationale and rejected alternatives: `2026-11-reinvent-booth-screen-v3.4-research.md` sections B1 and B3. Word-count limits respected; no other copy touched.

## 20. Polish pass v3.5 (Nov 16, 2026; wins over sections 13, 17, 18 and 19 where they conflict)

Seven-point Carlos review plus the pre-approved scene 8 adoption ("Keep the Dots" = red gate-dots kept). Copy is untouched; everything below is visual.

1. **Typography harmony (20.1):** the global h1 scale drops from clamp(80px, 8vw, 150px) to clamp(64px, 6.5vw, 122px) so all scene headlines sit one step smaller, and scene 2's line 1 rises from 5.6vw to the same 6.5vw (measured with the actual Red Hat Display metrics: "A billion AI agents by 2029." is 12.36 em wide, 80 percent of frame width at 6.5vw, so it stays on one line). Scene 2's content-wrapper gap drops from 60px to 22px, moving headline and sublines up against the datacenter blocks.
2. **Scene 3 six unique environments (20.2):** the 2x4 grid with repeated environments becomes a 3x2 grid of the six Carlos named, in scene 15's order (Physical, Virtual, Private cloud, Sovereign cloud, Public cloud, Edge). Boxes grow to 235x130 in a 760x280 viewBox. Icons are now the official Red Hat icon repository glyphs (assets/icons/*.png, 62px SVG images) centered at by+18, labels beneath at by+114 (17px), so text can never overlap an icon. Five red dots (r 5.5) keep pulsing in fixed clear-space spots around both.
3. **Scene 6 silicon strip (20.3):** "NVIDIA. AMD. Google TPUs. AWS Inferentia." now spans exactly the model-box width via SVG textLength=280 (lengthAdjust spacingAndGlyphs, 13px). The two model rectangles moved apart (self-hosted y 30 to 138, external y 196 to 290) to give the strip a 58px lane; the strip stays aligned to the gateway rectangle's vertical center (baseline y 172 for a rect spanning 30 to 290). Route lines and the gw-dots stream angles were retuned to the new box centers (y 84 and 243).
4. **Scene 11 X color (20.4):** the denial X is now #151515 (near-black), reading cleanly on the white rectangle fill it pops onto.
5. **Scene 5 DevOps icon (20.5):** the plain red circle is replaced by the repository's devops-586 glyph (150px img), with four Gray-10 dots floating through it in a trailing line (translate -95px to +95px, 3.6s, staggered 0.9s: agents one behind another). The old pulse-big keyframes are removed with their only user.
6. **Scene 13 density wall (20.6):** exactly 1,000 agent dots: 16 columns of 10 + c*7 dots (10, 17, ... 115, summing to 1000) rising from a shared baseline (y 262) to a shared ceiling (y 16). Dots shrink left to right (r 5.5 down to 1.3) and the per-column gap tightens so every column spans the same height: the left edge is countable chunky dots, the right edge is fine grain, and the mass reads as 1,000. The red control-plane dot above the chart is deleted (Carlos: out of place). Animation is grouped for kiosk performance: each column fades in on the 12.8s cycle staggered 0.35s (col-grow) and shimmers vertically +-2px on its own phase (col-shimmer), so the wall is never static and never ends frozen white; the whole cycle releases and rebuilds.
7. **Scene 15 repository icons (20.7):** the marquee's six hand-drawn SVG glyphs are replaced by the same six repository PNGs (60px SVG images at y 72) inside the `#env-set` def, so both marquee copies clone them. Ticks, labels and the static control line unchanged.
8. **Scene 8 adopts scene_gateway.png (20.8, pre-approved):** backdrop swapped from gen-scene08-badge.jpg (now spare) at opacity .85. The gate was PIL-measured on the new image: vertical glowing column peaking at x 58.4 percent, spanning y 3 to 99.7 percent. The pass/stop keyframes retarget 58.4 percent (pass continues to 68 and fades by 80; stop halts at 58.4 and fades in place). The nine dots move to the upper corridor (tops 14 to 66 percent) to stay clear of the red-lit cube cluster low-left (8.6 percent strongly-red pixels there), avoiding red-on-red. A calm right-edge gradient (transparent 70 percent to rgba(0,0,0,0.55) at 100) settles the bright lavender cube wall on the right third so the gate keeps the eye. Copy zone verified dark (top 40 percent average luminance 13.7).
9. **Scene 12 mantra uses the DevOps icon (20.9, v3.5.1):** the hand-drawn lemniscate, its five beat nodes and the two flow dots are replaced by the official devops-586 glyph (the same icon as scene 5), cropped to the glyph via viewBox `25 108 310 143`. Five Gray-20 agents (r 5) ride the stroke on a fitted figure-8 offset-path (M180,180 ... measured from the glyph: lobe centers x 50 and 310, vertical span 122 to 238, so the path stays inside the 11 to 19px stroke band), evenly spaced at 20 percent of the path (9s cycle, delays i*1.8s). The path is closed, so the train loops seamlessly with no fades. The per-beat node landing is retired: the words still land per beat, the loop is now continuous, which is calmer. Re-entry restart targets `.beat-word, .loop-dot`.

## 21. Copy pass v3.6 (Nov 16, 2026; supersedes the spine headlines in v3.4.1)

Value-based spine headlines, Carlos approved. Each headline carries its control word in Red Hat Red via an inline span (`color: var(--rh-red)`), visually linking headline, layer stack rows, and mantra beat words:

1. Scene 7: "Sandbox every agent." (Sandbox in red)
2. Scene 8: "Gate models, MCPs, and agents." (Gate in red). The breadth differentiator (keys, models, MCPs, agents) is split: headline names what passes through, support keeps "The agent never holds the key. The gateway does."
3. Scene 9: "Trace every decision." (Trace in red)
4. Scene 10: "Prove before production." (Prove in red); support becomes "Benchmarks. Red teaming. Every release." (evidence dropped as redundant with the headline verb; "Every release" adds continuous proof)
5. Scene 11: "One agent, one identity." (identity in red); support becomes "No shared accounts. No anonymous agents." (calls back to scene 3's ungoverned agents)

Layer stack rows and mantra beat words stay the locked nouns (Sandbox, Gateway, Traceability, Proof, Identity). All word limits respected. Scene 11's red word sits mid-sentence; its trailing period renders white like the other spine scenes.
