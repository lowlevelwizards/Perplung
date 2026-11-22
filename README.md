# Perplung

*A little world that discovers what it wants to become.*

**[Play the current experiment](https://lowlevelwizards.github.io/Perplung/)** · **[Living principles](./PRINCIPLES.md)**

## Body Study 03 — finding a gait that feels good

We are going atomic: making one cause and its effect feel good before adding another.

This is a small playable **GPU-rendered 3D character movement experiment**, not the full ecosystem. There is one little creature in a sunny clearing. Try barely nudging the thumbstick, walking, running, turning sharply, stopping, and hopping while moving.

- **Touch:** Move the thumbstick a little to amble, farther to walk, and all the way to run. Drag the scene to orbit; use two fingers to pinch-zoom or tap +/−. **Hop** works while another thumb is holding the stick. **Footprints** shows the optional, lightly colored planted contacts.
- **Keyboard/mouse:** WASD or arrows to run, Space to hop, R to reset, drag to orbit, scroll wheel or +/− buttons to zoom.
- **What we're testing:** Analogue movement speed, a gait whose foot cadence changes with speed, shorter legs and smaller feet, forward/back arm swing driven by leg position, a head that follows the body without making full spins, and physical hops that preserve horizontal momentum. Planted feet retain world positions and contact orientation, with corrective steps before the body stretches out of reach. Two-bone knee IK and bouncy secondary reactions remain.
- **Why the renderer changed:** The scene, ground, limbs, eyes, and body are now actual 3D triangle meshes rendered with WebGL depth testing. Occlusion is solved by the GPU instead of a fixed Canvas drawing order. The ground no longer relies on a projected polygon.
- **What we're not testing:** Quests, creatures, collectibles, ecosystem systems, or the final visual identity.

The experiment runs from `index.html` using built-in browser **WebGL**. It uses a small purpose-built mesh renderer rather than Three.js, so there is no runtime library or CDN dependency. WebGL support is required; software-only browsers that disable WebGL cannot render the scene. No external dependencies or build steps are needed. GitHub Pages publishes `main` from the repository root. No app installation or desktop development is needed to play from a phone.

## Previous playable worlds

The earlier game is **not deleted**. You can still play:

- [Body Study 02](./experiments/body-study-02.html) — first actual WebGL mesh/depth renderer
- [Body Study 01](./experiments/body-study-01.html) — the original Canvas-projected movement study
- [3D Living Brook](./experiments/living-brook-3d.html) — the previous integrated world, goals, and progress
- [2D Living Brook](./experiments/living-brook-2d.html) — the earlier ecosystem prototype
- [Sleeping Tree](./experiments/sleeping-tree-v2.html) — the three-place discovery prototype
- [First Meadow](./experiments/first-meadow.html) — our very first touch experiment

The body study does not use or overwrite the Living Brook's save slot.

**References:** The world-space contact and presentation-IK approach is informed by [Fieldwork3D's footstep scheduler](https://github.com/lowlevelwizards/Fieldwork3D/blob/main/src/breach-footsteps.ts), [Fieldwork3D's IK constraints](https://github.com/lowlevelwizards/Fieldwork3D/blob/main/src/breach-ik.ts), and [M3CH4's foot-contact controller](https://github.com/lowlevelwizards/M3CH4/blob/main/footContactController.js). Perplung uses its own deliberately tiny implementation.

## How we develop

Follow [the living principles](./PRINCIPLES.md). No fixed roadmap: play, notice, refine one interaction until it feels delightful, and only then decide what grows next.
