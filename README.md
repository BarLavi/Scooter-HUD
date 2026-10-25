# Scooter HUD

Portrait HUD for an e-scooter handlebar mount: big GPS speed, fighter-style horizon with lean (roll) arc, pitch tape (with % grade) and forward acceleration tape. Max speed / max acceleration / max braking are shown at the bottom and reset every time the app is opened.

## Put it on your phone (free, ~5 minutes)

Phone sensors and GPS only work over HTTPS, so host it on GitHub Pages:

1. github.com → **New repository** → name it e.g. `scooter-hud`, Public → Create.
2. **Add file → Upload files** → drag in all files from this folder (`index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`) → Commit.
3. **Settings → Pages** → Source: *Deploy from a branch*, Branch: `main` / root → Save.
4. After a minute, open `https://<your-username>.github.io/scooter-hud/` in **Chrome on the phone**.
5. Chrome menu ⋮ → **Add to Home screen / Install app**. It now opens fullscreen and works offline.

Test on a desk first: add `?demo` to the URL to see the screen move with fake data.

## Using it

- **START** → allow location.
- Put the phone in the mount, scooter standing upright on flat ground, **hold ZERO ~1 s** (progress bar fills, phone buzzes). The button pulses amber until you've zeroed since opening the app.
- Lean: arc at the bottom, pointer swings to the side you lean, digital readout in degrees L/R (amber above 30°).
- Pitch tape (left): degrees nose up/down, plus road grade %.
- Accel tape (right): forward g, + accelerating, − braking (amber below −0.3 g).
- Max values only update while riding (GPS > 4 km/h), so pulling the phone out of the mount won't spike them. Hold the max panel 2 s to clear them mid-day.
- Screen stays on while the app is open.

## Notes

- GPS speed updates about once per second and lags slightly; the dot top-left shows fix quality (green ≤10 m, amber ≤25 m, red = poor/lost).
- After editing any file, change `VERSION` in `sw.js` so the installed app picks up the update.
