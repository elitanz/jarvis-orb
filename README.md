# J.A.R.V.I.S. — Arc Reactor

**Live:** https://elitanz.github.io/jarvis-orb/

A standalone version of the JARVIS orb HUD. It runs entirely in the browser —
no server, no Python, no Mac. Open the link on any machine with Chrome,
including a school Chromebook.

## What it does

Tap once to engage. If you allow the microphone, the reactor reacts to your
voice in real time:

| You | Reactor |
|---|---|
| silence | **idle** — slow orange drift |
| start talking | **listening** — spins up, lighter orange |
| keep talking | **recording** — red, faster, core pulses to your volume |
| stop talking | **thinking** — gold, radar sweep |
| then | **speaking** — pale orange, prints a line |

Deny the mic (or if school policy blocks it) and the exact same state machine
runs off a synthetic signal instead, so it loops the full cycle on its own.

## Keys

- **F** — fullscreen
- **M** — mute the mic and fall back to the demo cycle
- `?auto=1` — skip the tap gate (kiosk / screenshots; always demo mode, since
  a mic needs a real user gesture)

## Notes

- Three.js loads from a CDN, so it needs internet — but nothing else.
- Pixel ratio is capped at 1.5, and if the GPU can't hold 40fps it drops to 1x
  once, automatically. That keeps it smooth on low-power laptops.
- Nothing is recorded, stored, or sent anywhere. The mic signal is only ever
  read as a volume number in the page and never leaves the browser.

Derived from the orb in the main JARVIS assistant, with the WebSocket link to
the local server replaced by the browser's own audio input.
