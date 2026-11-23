# Perplung

*A little world that discovers what it wants to become.*

**[Play the current experiment](https://lowlevelwizards.github.io/Perplung/)** · **[Living principles](./PRINCIPLES.md)**

## Bush Study 04 — sunlit layered bushes across the world

We are going atomic: making one cause and its effect feel good before adding another.

This is a small playable **GPU-rendered 3D environment and character experiment**, not the full ecosystem. The familiar rounded tiered bushes now continue well beyond the spawn clearing, inviting you to explore the wider ground without immediately leaving all vegetation behind.

- **Bush shape and shading:** B2's five horizontal, softly drooping foliage shelves are preserved. Their **tops are now lighter**, and lower tiers darker, to read as sunlit above and shaded below. Per-tier shade multipliers from bottom to top are `.82, .92, 1.02, 1.12, 1.22`. All bushes still share the same three rounded texture-atlas variants.
- **Placement and variation:** The original seven near-spawn bushes are preserved and joined by **343 deterministically placed relatives** across a roughly 192×192-unit region of the 220×220 ground. Every 24-unit patch generates a few bushes with jittered positions, gentle variations in scale, yaw, spread, height, tint, and phase. Rejection prevents overlaps and protects the immediate spawn. The world remains sparse rather than becoming a crowded forest.
- **Bush motion and performance:** The existing subtle, independently phased edge-only sway stays. All **350 bushes / 1,750 foliage cards** share one 512×128 alpha-cutout atlas and shader, with two tiny crossed stem cards per bush. Instead of drawing 350 separate bushes or one enormous uncullable mesh, they are baked once into **64 static spatial patch buffers**. Only nearby patches render—typically 4 near spawn and 5–8 along the wider world in focused travel tests. No new vegetation buffers are allocated while traveling. The vertex shader uses high precision to retain fine sway far from the origin.
- **Scope:** This pass extends this one established bush family rather than adding a new species or quests. Bushes remain visual-only without collision or interactions. The grass, small flowers, and existing rocks are still concentrated nearer the original clearing; those may be extended separately.
- **Touch:** Move the thumbstick a little to amble, farther to walk, and all the way to run. Drag the scene to orbit; use two fingers to pinch-zoom or tap +/−. The up-arrow button hops, even while your other thumb is moving. Footprints are always visible, with no toggle.
- **Keyboard/mouse:** WASD or arrows to run, Space to hop, R to reset, drag to orbit, scroll wheel or +/− buttons to zoom.
- **Grass:** Tufts are now **2.5× larger in both height and width**, with a more open fan of 4–5 rounded blades. The atlas widens the blade roots and fans the tips out farther, retaining four variants of the soft, chunky silhouette. Two crossed alpha-cutout texture cards provide volume without individual blade meshes. Atlas generation runs only once on startup, with no image downloads or build tools.
- **Wind:** Quiet, independently phase-shifted vertex-shader sway, slightly amplified to suit the larger tufts but still anchored at the root. No per-tuft or per-card CPU animation in the frame loop.
- **Grass batching:** The large tufts retain their deterministic distribution, with some excluded near the bushes so foliage does not crowd their bases. Four visibility-culled grass patches share one grass atlas and shader, using **ANGLE_instanced_arrays** where WebGL1 supports it or static patch batches otherwise. Both paths use at most four grass draw calls near the start.
- **Body:** Body Study 09's little human, shorter legs, more natural standing, and all movement/IK remain unchanged.
- **Slow-walk support:** Planted feet still replant before trailing too far, with compact forward landings. Step readiness, recovery swing time, and contact limits are adjusted for the shorter limbs, while preserving slow deliberate stepping. The body never stops to satisfy foot placement.
- **Gait:** At running speed, contacts still target the predicted touchdown pelvis, with lateral lead and quick bounded catch steps on sharp turns. Slow and fast walking share the same world-space IK and contact constraints; only timing, foot-placement lead and rear-support tolerance change with speed. Both feet never swing simultaneously.
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

- [Bush Study 03](./experiments/bush-study-03.html) — seven clustered bushes with dark upper tiers
- [Bush Study 02](./experiments/bush-study-02.html) — first stacked horizontal foliage-card bush
- [Bush Study 01](./experiments/bush-study-01.html) — original crossed upright leaf cards
- [Grass Pass 02](./experiments/grass-pass-02.html) — larger, airier rounded grass tufts
- [Grass Pass 01](./experiments/grass-pass-01.html) — original smaller, tighter grass tufts
- [Body Study 09](./experiments/body-study-09.html) — shorter legs and straighter resting posture
- [Body Study 08](./experiments/body-study-08.html) — slow-walk rear-foot recovery and support balance
- [Body Study 07](./experiments/body-study-07.html) — chest proportions, torso weight and faster foot placement
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
