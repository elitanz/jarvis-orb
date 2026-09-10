# J.A.R.V.I.S. — Arc Reactor

**Live:** https://elitanz.github.io/jarvis-orb/

A standalone version of the JARVIS orb HUD that **listens and talks back**. It
runs entirely in the browser — no server, no Python, no Mac. Open the link on
any machine with Chrome, including a school Chromebook.

## Talk to it

Tap once, allow the microphone, then say **"Jarvis, …"**. It transcribes what
you say, thinks, and answers out loud in a British voice.

| Say | It does |
|---|---|
| "Jarvis, what time is it?" | reads the real clock |
| "Jarvis, what day is it?" | reads the real date |
| "Jarvis, how's the battery?" | reads the real battery level |
| "Jarvis, status report" | reports the live frame rate |
| "Jarvis, go fullscreen" | actually goes fullscreen |
| "Jarvis, who are you?" | says what it is |
| anything else | tells you honestly that the thinking half is on the Mac |

The answers are a **local pattern matcher, not an AI**. It has no model behind
it and doesn't pretend to — the fallback line says so out loud.

## The reactor itself

Independently of the words, the orb reacts to your voice *volume* in real time:

| You | Reactor |
|---|---|
| silence | **idle** — slow orange drift |
| start talking | **listening** — spins up, lighter orange |
| keep talking | **recording** — red, faster, core pulses to your volume |
| stop talking | **thinking** — gold, radar sweep |
| answering | **speaking** — pale orange, pulses to the synthesized voice |

Deny the mic (or if school policy blocks it) and the same state machine runs
off a synthetic signal, so it loops the full cycle on its own.

## Keys

- **F** — fullscreen
- **M** — mute the mic and fall back to the demo cycle
- `?auto=1` — skip the tap gate (kiosk / screenshots; always demo mode, since
  a mic needs a real user gesture)

## Notes

- Speech recognition and synthesis are the browser's own Web Speech API —
  free, no key, no account. Chrome and ChromeOS only; Firefox won't listen.
- Three.js loads from a CDN, so it needs internet.
- Pixel ratio is capped at 1.5, and if the GPU can't hold 40fps it drops to 1x
  once, automatically. That keeps it smooth on low-power laptops.
- **Privacy:** audio is handled by the browser. Nothing is stored, and this
  page sends nothing anywhere — there is no backend to send it to. Note that
  Chrome's own speech recognition does the transcription on Google's servers,
  the same as any "click the mic" box on the web.

Derived from the orb in the main JARVIS assistant, with the WebSocket link to
the local server replaced by the browser's own audio input.
