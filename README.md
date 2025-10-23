# About AedosFX

AedosFX is a web-based Flutter application for sound processing and mixing using the `flutter_soloud` package. The goal is to provide a lightweight, browser-based mini DAW for quick prototyping and audio experimentation.

## Key features

- Grouping:
  - Elements (clips) inside a track
  - Tracks inside a bus or master
  - Buses inside the master
- Effects applied to elements, tracks, buses, or master:
  - EQ / shelf
  - Compressor / limiter
  - Reverb / delay
  - Shaper / shifter
  - Gain / fader
- Drag & drop of tracks into the app (browser)
- Supported file formats: wav, mp3, ogg, flac

## Typical workflows

- Quickly import a few tracks and set levels on the master
- Group drum parts into a bus, add compression and reverb sends
- Tweak effect order and EQ presets
- Layer loops and experiment with arrangement in the browser
- Export a mixdown (client-side or server-side, depending on implementation)

## Notes and implementation considerations

- `flutter_soloud` runs in the browser via WASM/WebAudio — watch for browser autoplay and permission constraints.
- Real-time mixing and effects can be CPU-heavy; profile performance when using many tracks/effects.
- Session persistence can use IndexedDB or exported JSON session files.
- Client-side mixdown requires buffering audio and generating a WAV file.

## Running locally (dev)

1. Clone the repository ```git clone https://github.com/miechoo/aedosfx.git```
1. Go to app directory ```cd app```
1. Get dependencies: ```flutter pub get```
1. Run in Chrome: ```flutter run -d chrome```
1. Build production web bundle: ```flutter build web```

## Project structure (suggested)
- app/          - Main flutter application
  - lib/
    - models/     — Track, Bus, Effect, Clip, Session models
    - audio/      — flutter_soloud wrappers, initialization, routing
    - widgets/    — UI components (track view, mixer, transport)
    - screens/    — main app screens
  - web/          — web assets and static files
  - test/         — unit and widget tests

## License

Specify a license (e.g., MIT) as appropriate.
