# SHMKD Aim Trainer — Standalone Aim Training Application

A premium, visually stunning aim training app built as a web application (packageable as a desktop .exe via Electron). The app helps players develop muscle memory, reaction time, and accuracy through multiple training modes with detailed analytics.

## Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Framework | **Vite + Vanilla JS** | Fast builds, lightweight, no framework overhead for a game-like app |
| Rendering | **HTML5 Canvas** | High-performance 2D rendering for smooth target movement |
| Styling | **Vanilla CSS** | Full control, custom design system, glassmorphism effects |
| Charts | **Chart.js** (via CDN) | Lightweight charting for performance analytics |
| Audio | **Web Audio API** | Hit/miss sound effects for feedback |
| Packaging | **Electron** (later) | Package as `.exe` when ready |

---

## Proposed Features & Pages

### 1. 🏠 Landing / Home Screen
- Animated hero with floating target particles
- Quick-start buttons for each training mode
- Today's stats summary card
- Recent session history

### 2. 🎯 Training Modes

#### a) **Flick Training**
- Targets spawn at random positions on canvas
- Click targets as fast as possible before they disappear
- Configurable: target size, spawn rate, lifetime, canvas area
- Tracks: accuracy, avg reaction time, hits/misses

#### b) **Tracking Training**
- A single target moves smoothly across the canvas (linear, sine wave, random)
- Player must keep cursor on the target — tracked via hover/proximity
- Configurable: target speed, size, movement pattern
- Tracks: % time on target, accuracy score

#### c) **Reaction Time Test**
- Screen changes color or a target appears after a random delay (1–5s)
- Player clicks as fast as possible
- Measures raw reaction time in milliseconds
- Shows distribution of results and average

#### d) **Speed Click Challenge**
- Multiple targets appear simultaneously
- Clear all targets as fast as possible
- Configurable: target count, target size
- Tracks: total clear time, accuracy, clicks per second

#### e) **Recoil Pattern Trainer**
- Displays common spray patterns as a visual guide
- Player must trace the counter-pattern with their mouse
- Scores based on deviation from ideal path
- Multiple preset patterns (vertical, horizontal, diamond, etc.)

### 3. 📊 Performance Dashboard
- Session history with filterable charts (Chart.js)
- Accuracy over time (line chart)
- Reaction time distribution (histogram)
- Mode-specific stats breakdown
- Personal bests & milestones
- All data stored in `localStorage`

### 4. ⚙️ Settings Panel
- Mouse sensitivity multiplier
- Crosshair customization (color, size, style)
- Target appearance (color, shape, size)
- Sound effects on/off
- Dark/Light theme toggle
- Difficulty presets (Easy, Medium, Hard, Custom)
- Reset stats option

---

## UI/UX Design Direction

- **Dark theme by default** with a sleek, gaming-inspired aesthetic
- **Glassmorphism cards** with subtle backdrop-blur effects
- **Accent color palette**: Electric cyan (`#00E5FF`) + Deep violet (`#7C4DFF`) gradient
- **Micro-animations**: Target pop-in/out, score fly-ups, smooth page transitions
- **Custom crosshair** rendered on canvas that replaces the default cursor
- **Google Fonts**: `Inter` for UI, `Orbitron` for headings (sci-fi/gaming feel)
- **Responsive layout**: Works on any screen size

---

## Project Structure

```
SHMKD/
├── index.html              # Entry point
├── package.json            # Vite config & scripts
├── vite.config.js          # Vite configuration
├── src/
│   ├── main.js             # App initialization & routing
│   ├── styles/
│   │   ├── index.css       # Global styles & design tokens
│   │   ├── home.css        # Home page styles
│   │   ├── training.css    # Training mode styles
│   │   ├── dashboard.css   # Dashboard styles
│   │   └── settings.css    # Settings styles
│   ├── pages/
│   │   ├── home.js         # Home/landing page
│   │   ├── flick.js        # Flick training mode
│   │   ├── tracking.js     # Tracking training mode
│   │   ├── reaction.js     # Reaction time test
│   │   ├── speed-click.js  # Speed click challenge
│   │   ├── recoil.js       # Recoil pattern trainer
│   │   ├── dashboard.js    # Performance dashboard
│   │   └── settings.js     # Settings panel
│   ├── core/
│   │   ├── canvas.js       # Canvas rendering engine
│   │   ├── target.js       # Target class (spawn, animate, hit detection)
│   │   ├── crosshair.js    # Custom crosshair renderer
│   │   ├── audio.js        # Sound effects manager
│   │   ├── stats.js        # Stats tracker & localStorage manager
│   │   └── router.js       # Simple SPA router
│   └── assets/
│       └── sounds/         # Hit/miss/start sound effects (generated)
├── public/
│   └── favicon.svg         # App icon
└── README.md
```

---

## Implementation Order

| Phase | Tasks | Est. Files |
|-------|-------|-----------|
| **Phase 1: Foundation** | Vite setup, design system (CSS), router, canvas engine | 6 files |
| **Phase 2: Core Training** | Flick mode, Target class, crosshair, hit detection, audio | 5 files |
| **Phase 3: More Modes** | Tracking, Reaction, Speed Click, Recoil trainer | 4 files |
| **Phase 4: Analytics** | Stats tracker, Dashboard with Chart.js, session history | 3 files |
| **Phase 5: Polish** | Settings panel, Home page, animations, sound effects | 4 files |

---

## Verification Plan

### Automated
- `npm run dev` — Verify dev server starts without errors
- `npm run build` — Verify production build completes

### Manual
- Launch each training mode and verify gameplay mechanics
- Test hit detection accuracy on canvas
- Verify stats persist across page reloads (localStorage)
- Check responsive layout on different window sizes
- Verify crosshair rendering and cursor replacement
- Test settings changes apply in real-time

---

## Open Questions (To resolve before building)
- Include Electron (.exe) packaging in initial build, or as a follow-up phase?
- Any specific game's recoil patterns to include, or generic patterns only?
- Preferred accent colors, or go with the proposed cyan/violet palette?
