# Jumping Tab

A slopsmith plugin that adds a Yousician-style 2D horizontal tab view to the player. Notes flow right-to-left toward a glowing hit line, trajectory arcs connect consecutive monophonic notes, and a glowing ball visibly hops along those arcs and squashes when it crosses the hit line.

## Install

Clone into your slopsmith `plugins/` directory and restart the web service:

```bash
cd /path/to/slopsmith/plugins
git clone <this-repo> jumpingtab
cd ..
docker compose restart web
```

Hard-reload the browser. A **Jumping Tab** button will appear in the player controls when a song is loaded.

## Use

1. Pick a song from your library.
2. Wait for the button to become enabled (song data loading).
3. Click **Jumping Tab** — the 3D highway is replaced with the 2D tab view.
4. Press play. Watch the ball hop.
5. Click the button again to return to the standard highway.

## What it supports

- 6-string guitar and 4-string bass arrangements (auto-detected from tuning length).
- Respects whichever arrangement is currently selected in slopsmith's player.
- Smooth sync to slopsmith's audio playback time.
- Sustain notes drawn as tails.
- Past notes fade out ~0.4 seconds after crossing the hit line.

## What it doesn't do (yet)

- No chord name labels.
- No technique glyphs (bend / slide / hammer-on / pull-off visuals — the notes still render, just as plain circles).
- No chord-shape diagrams.
- No microphone input or scoring.
- No settings panel for speed / colors / visibility window.
- No standalone full-screen mode — it's a player overlay.

## Tests

`plugins/jumpingtab/test/test.html` is a standalone browser test harness for the pure helpers (layout math, binary search, trajectory builder, bezier). Open the file directly in a browser:

```
file:///<path-to>/slopsmith/plugins/jumpingtab/test/test.html
```

All assertions should report green; the page title shows `N pass / 0 fail`.

Rendering, animation, and plugin integration are verified manually — there is no automated harness for those.
