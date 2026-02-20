# csa-js

![version](https://img.shields.io/badge/version-0.1-orange)
![size](https://img.shields.io/badge/size-49kb-blue)
---

## Installation

```html
<script src="csa.js"></script>
```

---

## API

### `csa.player(opts)`

Core method. Returns a player instance.

```js
const p = csa.player({
  src: 'video.mp4',
  title: 'My Video',
  mode: 'modal',         // 'modal' | 'card' | 'box'
  thumbnail: 'thumb.jpg',
  autoplay: false,
  muted: false,
  loop: false,
  loader: 'ring',        // 'ring' | 'bars' | 'dots' | 'shimmer' | 'gif' | 'custom'
  loaderGif: 'load.gif', // required when loader is 'gif'
  loaderHTML: '',        // required when loader is 'custom'
  qualities: [           // optional multi-quality
    { label: '1080p', src: 'video-1080.mp4' },
    { label: '720p',  src: 'video-720.mp4'  },
  ],
  defaultQuality: 0,
  subtitle: {
    src: 'subs.vtt',
    color: '#ffffff',
    bg: 'rgba(0,0,0,0.72)',
    opacity: 1,
    size: 16,
  },
  theme: {
    accent: '#e8ff47',
    accent2: '#47b8ff',
    bg: '#09090f',
    surface: '#111119',
    radius: '14px',
  },
  errorIcon: '⚠️',
  errorMessage: 'Failed to load video.',
  onClose: () => {},
  onEnd: () => {},
});
```

---

### Shorthand methods

```js
csa.modal(src, title, opts)  // opens in modal (default wide)
csa.card(src, title, opts)   // opens in card (medium)
csa.box(src, title, opts)    // opens in box (compact)
```

---

### `csa.from(element, opts)`

Binds a click handler to a DOM element.

```js
csa.from(document.querySelector('#btn'), { src: 'video.mp4' });
```

Or via HTML attributes:

```html
<button data-csa data-csa-src="video.mp4" data-csa-title="Title" data-csa-mode="modal">
  Play
</button>
```

---

### `csa.init()`

Auto-binds all `[data-csa]` elements in the document.

```js
csa.init();
```

---

### `csa.closeAll()`

Closes all active player instances.

---

## Instance methods

| Method | Description |
|---|---|
| `p.play()` | Start playback |
| `p.pause()` | Pause playback |
| `p.seek(seconds)` | Seek to time |
| `p.setVolume(0–1)` | Set volume |
| `p.setSpeed(rate)` | Set playback rate (e.g. `1.5`) |
| `p.setLoop(bool)` | Enable or disable loop |
| `p.setQuality(index)` | Switch quality by index |
| `p.setLoader(type)` | Change loader type at runtime |
| `p.setMode(mode)` | Change display mode at runtime |
| `p.loadSubtitle(src)` | Load a VTT subtitle file or raw VTT string |
| `p.addCue(start, end, text)` | Add a single subtitle cue |
| `p.setSubtitleStyle(opts)` | Update subtitle appearance (`color`, `bg`, `opacity`, `size`) |
| `p.debug(bool?)` | Toggle or set debug console visibility |
| `p.info()` | Returns current player state as an object |
| `p.close()` | Close and destroy the player |

---

## Keyboard shortcuts

| Key | Action |
|---|---|
| `Space` / `K` | Play / Pause |
| `Arrow Right` | Seek +5s |
| `Arrow Left` | Seek -5s |
| `Arrow Up` | Volume +10% |
| `Arrow Down` | Volume -10% |
| `M` | Mute toggle |
| `F` | Fullscreen toggle |
| `Escape` | Close settings or player |

---
