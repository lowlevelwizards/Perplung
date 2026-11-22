# Perplung

*A little world that discovers what it wants to become.*

**[Play the current experiment](https://lowlevelwizards.github.io/Perplung/)** · **[Living principles](./PRINCIPLES.md)**

## Body Study 07 — feet, weight and a better chest

We are going atomic: making one cause and its effect feel good before adding another.

This is a small playable **GPU-rendered 3D character movement experiment**, not the full ecosystem. There is one small human character in a sunny clearing. Try walking, running, stopping, turning, and quick hops while moving.

- **Touch:** Move the thumbstick a little to amble, farther to walk, and all the way to run. Drag the scene to orbit; use two fingers to pinch-zoom or tap +/−. The up-arrow button hops, even while your other thumb is moving. Footprints are always visible, with no toggle.
- **Keyboard/mouse:** WASD or arrows to run, Space to hop, R to reset, drag to orbit, scroll wheel or +/− buttons to zoom.
- **Body:** The oversized head, short neck and simplified human anatomy remain. The chest is now a low, rounded cylinder with a gentle shoulder/waist taper, rather than a second sphere. The pelvis, shoulders, lower arms and shoes are modestly rebalanced.
- **Gait:** At running speed, new foot contacts are aimed at the **predicted touchdown pelvis**, with lateral lead for changes of direction. Slow steps retain their previous deliberate placement. Swinging feet can still make small midair corrections, while planted feet remain grounded within the reachable support range. **Sharp turns use quicker, bounded catch steps** so an anchored support foot does not need to drag behind. Body movement never stalls to accommodate foot placement.
- **Physical animation:** Grounded IK, spring-damped vertical center-of-mass travel, small side-to-side load rocking, and pelvis/chest counter-twist. They follow actual foot contact and turning instead of an unrelated time-based bob. Arm swing stays tied to the opposite leg.
- **Hop:** A shorter, sharper arc, still available while moving.
- **Display:** Only the tiny version indicator and essential touch controls appear. Light fading footprints remain on by default; opaque yellow/green foot-contact debugging dots have been removed.
- **Preserved:** Body momentum, damped weight response, 3D depth, IK, mobile frame-time substeps, and camera orbit/zoom.
- **Play-space:** There is no artificial circular movement boundary in this study. The ground extends far beyond the small decorated clearing. Movement and camera controls remain unchanged.
- **Why the renderer changed:** The scene, ground, limbs, eyes, and body are now actual 3D triangle meshes rendered with WebGL depth testing. Occlusion is solved by the GPU instead of a fixed Canvas drawing order. The ground no longer relies on a projected polygon.
- **What we're not testing:** Quests, creatures, collectibles, ecosystem systems, or the final visual identity.

The experiment runs from `index.html` using built-in browser **WebGL**. It uses a small purpose-built mesh renderer rather than Three.js, so there is no runtime library or CDN dependency. WebGL support is required; software-only browsers that disable WebGL cannot render the scene. No external dependencies or build steps are needed. GitHub Pages publishes `main` from the repository root. No app installation or desktop development is needed to play from a phone.

## Previous playable worlds

The earlier game is **not deleted**. You can still play:

- [Body Study 06](./experiments/body-study-06.html) — first little-human rig and minimal HUD
- [Body Study 05](./experiments/body-study-05.html) — smoother body momentum and contact handling
- [Body Study 04](./experiments/body-study-04.html) — previous running-bounce and contact experiment
- [Body Study 03](./experiments/body-study-03.html) — previous WebGL gait and proportions
- [Body Study 02](./experiments/body-study-02.html) — first actual WebGL mesh/depth renderer
- [Body Study 01](./experiments/body-study-01.html) — the original Canvas-projected movement study
- [3D Living Brook](./experiments/living-brook-3d.html) — the previous integrated world, goals, and progress
- [2D Living Brook](./experiments/living-brook-2d.html) — the earlier ecosystem prototype
- [Sleeping Tree](./experiments/sleeping-tree-v2.html) — the three-place discovery prototype
- [First Meadow](./experiments/first-meadow.html) — our very first touch experiment

The body study does not use or overwrite the Living Brook's save slot.

**References:** The world-space contact and presentation-IK approach is informed by [Fieldwork3D's footstep scheduler](https://github.com/lowlevelwizards/Fieldwork3D/blob/main/src/breach-footsteps.ts), [Fieldwork3D's IK constraints](https://github.com/lowlevelwizards/Fieldwork3D/blob/main/src/breach-ik.ts), and [M3CH4's foot-contact controller](https://github.com/lowlevelwizards/M3CH4/blob/main/footContactController.js) and [articulation motion](https://github.com/lowlevelwizards/M3CH4/blob/main/articulationMotion.js). Perplung uses its own deliberately tiny implementation.

## How we develop

Follow [the living principles](./PRINCIPLES.md). No fixed roadmap: play, notice, refine one interaction until it feels delightful, and only then decide what grows next.
