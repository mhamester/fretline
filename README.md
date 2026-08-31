# TabTrain 🎸

**Load it. Play it. Check it.**

A free, browser-based guitar tab practice tool with real-time pitch detection. Paste in a tab, watch the notes scroll toward you in a waterfall display, and play along — TabTrain listens through your microphone and tells you whether you actually hit the right note, in time.

No install, no signup, no ads. Runs entirely in your browser — your audio never leaves your device.

**[Try it live →](https://mhamester.github.io/tabtrain/)**

---

## Features

- 🌊 **Waterfall display** — notes scroll toward a hitline in real time, synced to an adjustable BPM and metronome, so you always know what's coming next
- 📜 **Classic tab view** — prefer reading standard 6-line ASCII tab notation? Toggle to it any time, fully synced with the waterfall
- 🎯 **Real pitch detection** — uses the YIN pitch-detection algorithm plus onset (fresh-pluck) detection, not just volume, so it can tell a genuine repeated note from a string still ringing out
- ⏸ **Wait mode** — pauses and waits for you to get a note right instead of marching on, ideal for beginners; toggle off for strict-tempo practice
- 🔁 **Loop** — automatically repeats a section or the whole song for focused practice
- ⏱ **Timing calibration** — measures your device's real-world audio latency against a visual/audio reference and corrects for it, so "on time" actually means on time
- 📋 **Multi-section tabs** — paste a full song with `[Verse]`, `[Chorus]`, etc., and jump between sections with a picker, or play the whole thing continuously
- ▶ **Tab preview playback** — hear a synthesized preview of what a tab sounds like before you try to play it
- 🎚️ **Mic sensitivity control** — adjustable gain for quiet pickups or distant mics
- 🎼 **Scales practice** — minor pentatonic and blues scale, generated as a movable "box 1" shape at any root fret you choose, so you can drill the pattern in any key

## How to use it

1. Pick a song from the library, generate a scale run (set a root fret for minor pentatonic or blues), or paste your own tab into the import box (standard ASCII format: 6 lines, `e|--3--0--|` style)
2. Hit **Start Practice** — allow microphone access when prompted
3. Play along as notes cross the waterfall's hitline
4. Notes turn green when you play them correctly, red when you miss the timing window

Works on iPhone, Android, and desktop browsers. On mobile, use "Add to Home Screen" from your browser's share menu for an app-like experience.

## Tech notes

TabTrain is a single self-contained HTML file — no build step, no dependencies, no backend. It uses:

- **Web Audio API** for microphone input and audio synthesis (metronome clicks, tab preview playback)
- **YIN algorithm** for pitch detection, with a context-aware search that checks near the expected note first to avoid octave errors
- **Custom onset detection** (loudness-spike analysis) to distinguish a fresh pluck from a sustained ring-out
- Everything runs client-side — no data is sent anywhere, ever

## Running it locally / deploying your own copy

This is a static site — no build process required:

```bash
git clone https://github.com/mhamester/tabtrain.git
cd tabtrain
# open index.html directly in a browser, or serve it locally:
python3 -m http.server 8000
```

To deploy your own copy on GitHub Pages: fork the repo, go to **Settings → Pages**, and set the source to your `main` branch.

## Known limitations

- Chord detection (multiple simultaneous notes) isn't supported — true polyphonic pitch detection from a single microphone is a hard problem, so TabTrain currently focuses on single-note tabs
- Guitar technique symbols (hammer-ons, slides, bends) in tab notation are tolerated but not interpreted
- Timing is inferred from character spacing in the tab, since plain ASCII tab doesn't encode rhythm natively — a "16th note" vs "8th note" grid setting lets you match this to how a given tab was written

## Contributing

Issues and pull requests welcome. This is a hobby project built for personal guitar practice — no roadmap promises, but improvements are always appreciated.

## License

MIT — do whatever you'd like with it.
