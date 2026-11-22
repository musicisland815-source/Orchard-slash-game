# Orchard Slash

A bright, responsive browser-based fruit-slicing arcade mini-game built with HTML5 Canvas, TypeScript, React, Vite, and Tailwind CSS. Runs completely client-side as a static site with zero backend, database, or API keys.

## Gameplay & Features

- **Responsive Slicing Controls**:
  - **Mouse**: Click and drag across flying fruit.
  - **Touch**: Swipe smoothly across the playfield (`touch-action: none` prevents accidental page scrolling inside the game area).
  - **Keyboard**: Move the reticle with **Arrow Keys** or **WASD**, press/hold **Space** to slash, **P** or **Esc** to pause, **M** to mute, **R** to restart.
- **Combo & Streak System**:
  - Slice **3 or more fruits** in a single swift swipe to earn escalating combo bonuses (`3x COMBO`, `4x BLITZ`, `5x FRENZY`, `6x ULTRA`).
  - Maintain consecutive slices without dropping fruit to build up to a **3x Streak Multiplier**.
  - Slice rare **Golden Starfruits** for `+50` base points and `+3s` bonus clock time.
- **Avoid Bombs**:
  - Sparking iron bombs carry a crimson `X` danger emblem and pulsing warning halo.
  - Slicing a bomb deducts **1 Life** (out of 3) and **25 points**, and resets your streak. Losing all 3 lives ends the round early.
- **Procedural Web Audio**:
  - Synthesized slice snaps, blade whooshes, combo chimes, countdown ticks, and bomb explosions created via Web Audio API only after user interaction, with a persistent mute toggle.

## Local Development & Testing

```bash
# Install dependencies
npm install

# Run unit tests for game rules, collision math, and scoring
npx --yes tsx --test src/game/rules.test.ts

# Start local dev server (http://localhost:3000)
npm run dev

# Typecheck and create production static build
npm run lint
npm run build
```

## Deploying to Vercel

This project builds into a pure static bundle in `dist/` and includes `vercel.json`.

### Option 1: Vercel CLI

```bash
npm i -g vercel
vercel
```

Follow the prompts (build command: `npm run build`, output directory: `dist`). To deploy directly to production:

```bash
vercel --prod
```

### Option 2: Git Integration

1. Push this repository to GitHub, GitLab, or Bitbucket.
2. Import the repository in the Vercel dashboard.
3. Keep the detected **Vite** preset (`npm run build` -> `dist`) and click **Deploy**. No environment variables are required.
