# Perplung

*A little world that discovers what it wants to become.*

**[Play the current experiment](https://lowlevelwizards.github.io/Perplung/)** · **[Living principles](./PRINCIPLES.md)**

## Body Study 01 — one little step

We are going atomic: making one cause and its effect feel good before adding another.

This is a small, playable **3D character movement experiment**, not the full ecosystem. There is one little creature on one sunny patch of ground. Try walking, stopping, reversing, pivoting, and taking a small hop.

- **Touch:** Move with the thumbstick; drag the scenery to orbit the camera; tap **Hop** for a little jump. Tap **Footprints** to see planted contacts.
- **Keyboard:** WASD or arrow keys to move, Space to hop, R to reset, drag to orbit.
- **What we're testing:** The body has acceleration and braking. Feet plant in world space, swing to new placements, and use two-bone IK for knees. Body weight, head and ears, arms, and impact recovery react to movement. The gait should stop when movement stops.
- **What we're not testing:** Quests, creatures, collectibles, ecosystem systems, or the final visual identity.

The experiment runs from `index.html` with built-in browser Canvas, no external dependencies or build steps. GitHub Pages publishes `main` from the repository root. No app installation or desktop development is needed to play from a phone.

## Previous playable worlds

The earlier game is **not deleted**. You can still play:

- [3D Living Brook](./experiments/living-brook-3d.html) — the previous integrated world, goals, and progress
- [2D Living Brook](./experiments/living-brook-2d.html) — the earlier ecosystem prototype
- [Sleeping Tree](./experiments/sleeping-tree-v2.html) — the three-place discovery prototype
- [First Meadow](./experiments/first-meadow.html) — our very first touch experiment

The body study does not use or overwrite the Living Brook's save slot.

## How we develop

Follow [the living principles](./PRINCIPLES.md). No fixed roadmap: play, notice, refine one interaction until it feels delightful, and only then decide what grows next.
