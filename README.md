# musepai-library

Metadata for every track the ACE-Step daily pipeline generates. **Private.**

One directory per day, one JSON per track, plus the day's `index.json`:

```
2026-09-21/
├── index.json            the day's catalogue
└── a669cd99443b.json     one track
```

Media is referenced **by filename**, never by URL:

```json
{
  "id": "a669cd99443b",
  "title": "Hati Yang Tetap Menunggu",
  "genre": "bossa nova",
  "language_name": "Indonesian",
  "lyrics": "…",
  "background": "…",
  "audio": "a669cd99443b.mp3",
  "cover": "a669cd99443b.webp",
  "mv":    "a669cd99443b.mp4"
}
```

That is what makes this repo portable: the server resolves those names
against whatever media root it is configured with — a synced directory or a
CDN — so moving to a different host costs nothing here.

No media in this repository. See `.gitignore`.

## Filling things in later

This is the half that keeps changing. Correcting lyrics, adding cover art,
writing a track's background, reclassifying a genre — edit the track's JSON,
rebuild the day's `index.json`, commit. The server picks it up on its next
pull.

## Who writes here

`deploy/publish-library.sh` in the MusePAI repo, after each clean daily run.
It rsyncs the JSON out of the generation directory, commits and pushes.
