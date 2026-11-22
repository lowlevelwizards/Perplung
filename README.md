# Perplung

*A little world that discovers what it wants to become.*

**[Play the current experiment](https://lowlevelwizards.github.io/Perplung/)** · **[Living principles](./PRINCIPLES.md)**

## Body Study 02 — the body is really 3D

We are going atomic: making one cause and its effect feel good before adding another.

This is a small playable **GPU-rendered 3D character movement experiment**, not the full ecosystem. There is one little creature on one sunny patch of ground. Try walking, stopping, reversing, pivoting, and taking a small hop.

- **Touch:** Move with the thumbstick; drag the scenery to orbit the camera; tap **Hop** for a little jump. Tap **Footprints** to see planted contacts.
- **Keyboard:** WASD or arrow keys to move, Space to hop, R to reset, drag to orbit.
- **What we're testing:** The body has acceleration and braking. Only one foot swings at a time; the other remains planted in world space. Planted feet retain their orientation until they replant, and the body cannot pull a supporting foot past the leg's physical reach. Two-bone IK positions the knees. Weight shifts, head, ears, arms, and landing recovery react to movement.
- **Why the renderer changed:** The scene, ground, limbs, eyes, and body are now actual 3D triangle meshes rendered with WebGL depth testing. Occlusion is solved by the GPU instead of a fixed Canvas drawing order. The ground no longer relies on a projected polygon.
- **What we're not testing:** Quests, creatures, collectibles, ecosystem systems, or the final visual identity.

The experiment runs from `index.html` using built-in browser **WebGL**. It uses a small purpose-built mesh renderer rather than Three.js, so there is no runtime library or CDN dependency. WebGL support is required; software-only browsers that disable WebGL cannot render the scene. No external dependencies or build steps are needed. GitHub Pages publishes `main` from the repository root. No app installation or desktop development is needed to play from a phone.

## Previous playable worlds

The earlier game is **not deleted**. You can still play:

- [Body Study 01](./experiments/body-study-01.html) — the original Canvas-projected movement study
- [3D Living Brook](./experiments/living-brook-3d.html) — the previous integrated world, goals, and progress
- [2D Living Brook](./experiments/living-brook-2d.html) — the earlier ecosystem prototype
- [Sleeping Tree](./experiments/sleeping-tree-v2.html) — the three-place discovery prototype
- [First Meadow](./experiments/first-meadow.html) — our very first touch experiment

The body study does not use or overwrite the Living Brook's save slot.

**References:** The world-space contact and presentation-IK approach is informed by [Fieldwork3D's footstep scheduler](https://github.com/lowlevelwizards/Fieldwork3D/blob/main/src/breach-footsteps.ts), [Fieldwork3D's IK constraints](https://github.com/lowlevelwizards/Fieldwork3D/blob/main/src/breach-ik.ts), and [M3CH4's foot-contact controller](https://github.com/lowlevelwizards/M3CH4/blob/main/footContactController.js). Perplung uses its own deliberately tiny implementation.

## How we develop

Follow [the living principles](./PRINCIPLES.md). No fixed roadmap: play, notice, refine one interaction until it feels delightful, and only then decide what grows next.
