# Naruto — Rasengan Hand-Tracking Web App

Summon a Rasengan above your palm, Naruto-style — right in the browser. The app
turns on your webcam, tracks your hands with MediaPipe, and charges a glowing
Rasengan orb over your open palm.

**Live demo:** https://pradhan-07.github.io/Naruto/

## How it works

- Open your palm in front of the camera — the Rasengan charges up and floats
  above your hand. Close your fist and it fades away.
- Works with **both hands at once** — each hand gets its own orb.
- A glowing hand skeleton is drawn over each hand so you can see the tracking
  live: the left hand in warm Naruto orange, the right hand in cool chakra blue.

## Features

- **Hand tracking** — MediaPipe Hands, up to 2 hands, `modelComplexity: 1`,
  detection and tracking confidence 0.65.
- **Open-palm detection** — a palm counts as open when 3 or more fingers are
  extended (fingertip farther from the wrist than its knuckle). The orb's
  charge rises while the palm is open and decays when it closes or the hand
  leaves the frame.
- **Rasengan orb** — a looping video (`assets/rasengan.mp4`) placed above the
  palm centre, sized to the hand and lifted in proportion to hand size, with a
  `screen` blend mode so it glows over the camera feed.
- **Mirrored selfie-style camera** (1280×720) with a vignette overlay and a
  hint pill at the bottom.

## Tech stack

- Plain HTML, CSS and JavaScript — no build step, no framework.
- MediaPipe Hands, Camera Utils and Drawing Utils, loaded from the jsDelivr CDN.
- `assets/rasengan.mp4` — the looping Rasengan orb video.

## Run it

### Live

Open https://pradhan-07.github.io/Naruto/ and allow camera access.

### Locally

Serve the folder over HTTP (camera access needs localhost or HTTPS), then open
it in a browser and allow camera access:

```bash
# from the repo root
python3 -m http.server 8000
# then open http://localhost:8000
```

## Project structure

```
Naruto/
├── index.html          # the whole app: camera, hand tracking, skeleton + orb rendering
├── assets/
│   ├── rasengan.mp4    # looping Rasengan orb video
│   └── assets.gitkeep
└── README.md
```

## Notes

- Needs a webcam and an internet connection (MediaPipe libraries load from the
  jsDelivr CDN).
- Best in a well-lit room with your hands clearly visible to the camera.

## Author

Karan Kumar Pradhan — https://pradhan.runs-on.dev/
