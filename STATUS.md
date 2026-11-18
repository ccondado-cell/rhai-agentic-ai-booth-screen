# STATUS — reinvent-booth-screen

> Handoff file: whoever touches work last updates this before ending a session
> (done / in-flight / next / how to verify).

## Done
- v3.7 copy pass (2026-11-18): two support-line swaps from field feedback —
  scene 7 "Its blast radius ends where policy draws it." → "If an agent
  misbehaves, it goes nowhere else."; scene 9 "Tested against attacks first."
  → "Tested against attacks." Word-count limits respected (8 and 6 words;
  limit 12; no em or en dashes). Copy doc gained the v3.7 entry; README lock
  bumped.
- v3.7.1 scene 12 visual pass (2026-11-18): the five agents now ride inside
  the DevOps glyph's red stroke instead of floating outside it. The old
  offset-path was a hand-fitted figure-eight; the new one is traced from the
  glyph's own red channel (distance-transform ridge of the stroke, 705 units,
  103 points, every sample ≥ 5.68 units from the stroke edge). Dot radius 5 →
  4.5 so the disc fits everywhere. Because the real stroke is open, the train
  now fades in at the tapered end of the right lobe and fades out where the
  loop runs into the return arrow. The dot delays are negative (same 1.8s
  spacing) so all five agents are spread around the stroke the moment the
  scene opens: the scene lasts 6.4s and five agents at 1.8s apart need 7.2s,
  so with positive delays the fifth never appeared.
  Details: `docs/addendum.md` section 22.
- Both copies of `index.html` are in sync at v3.7.1.

## In flight
- None.

## Next
- Sanity-check scene 12 on the actual booth screen (or any browser) once: the
  fade timing at the two stroke ends is the only thing pixels can't prove —
  if the dissolve into the arrow reads as a blink, shorten the last fade from
  5% to 3% in `@keyframes loop-train`.
- If the spoken presenter track references "blast radius" or "attacks first,"
  sync its script with v3.7 wording before booth rehearsal.

## How to verify
- Live: https://ccondado-cell.github.io/rhai-agentic-ai-booth-screen/ — view
  source; scene 7 support reads "If an agent misbehaves, it goes nowhere else."
  and the `.loop-dot` offset-path starts `M206.0,206.5`.
- Scene 12: open `index.html` and step to scene 12 — the five gray dots must
  stay inside the red stroke the whole way round, appearing out of the open
  end of the right lobe and dissolving where the loop meets the arrow.
- Local: press right arrow twice past the intro to reach scene 7 (presenter mode).
