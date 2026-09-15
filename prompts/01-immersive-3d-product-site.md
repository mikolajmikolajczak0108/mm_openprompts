# Immersive 3D product website

This is the full prompt used as the basis for the Loki Bone 3D website shown in the demo.

It assumes a real GLB model is available and works especially well together with the `immersive-3d-web` Claude Code skill:

https://github.com/gabremoku/immersive-3d-web

## Prompt

You are acting as a senior creative developer, 3D web engineer, motion designer and art director.

Your task is to build a production-quality immersive 3D product website for a dog toy called:

LOKI BONE

This is NOT a conventional SaaS landing page.
This is NOT a template.
This is NOT a generic AI-generated website.

The goal is an Awwwards-quality immersive WebGL product experience in the style of modern cinematic 3D product websites, with scroll-driven storytelling, premium product rendering and aggressive art direction.

The website exists primarily as a visual showcase / fictional advertising campaign for Loki's red rubber chew toy.

I will provide the real 3D model generated from Hunyuan3D.

Assume the file is located at:

/public/models/loki-bone.glb

THIS MODEL IS THE HERO OF THE ENTIRE WEBSITE.

Do not replace it with:

a primitive

a placeholder

an image

a generic bone model

a recreated approximation

Use the actual GLB.

Before implementing animations:

Inspect the GLTF scene hierarchy.

Inspect meshes, materials, dimensions and origin.

Correct centering/orientation in code if necessary.

Preserve the original proportions.

Preserve texture/detail from the source model.

Do not destructively simplify the model.

If the GLB contains multiple separate meshes for the central rings, expose them individually for animation.

If it is a single merged mesh, DO NOT fake an exploded view by breaking or visually corrupting the geometry.

Use:

React
TypeScript
Vite
Three.js
@react-three/fiber
@react-three/drei
GSAP
GSAP ScrollTrigger
Lenis
@react-three/postprocessing

Use modern versions that are mutually compatible.

Do not use Spline.

The Three.js / R3F scene should remain persistent between major sections instead of constantly destroying and recreating the WebGL canvas.

Use one cinematic 3D scene whose:

camera

model

lights

material response

depth

background

post-processing

change progressively through the experience.

Think:

Awwwards Site of the Day
experimental product website
cinematic commercial
Nike product reveal
Apple product cinematography
high-end automotive microsite
fashion campaign
WebGL scrollytelling

BUT do not copy the visual identity of any existing brand.

The product itself should feel absurdly premium even though it is a dog toy.

Brand mood:

CHAOTIC
PLAYFUL
PREMIUM
SLIGHTLY AGGRESSIVE
DOG ENERGY
MINIMAL COPY
MAXIMUM VISUAL IMPACT

Primary colors:

near-black / charcoal
warm off-white
deep saturated rubber red

The red toy must dominate the color palette.

Avoid rainbow gradients.

Avoid excessive glassmorphism.

Avoid generic rounded SaaS cards.

Avoid the typical AI website look.

Avoid icons unless absolutely necessary.

Do not fill the site with UI.

Let the 3D object, typography, scale and motion create the design.

Use a bold premium grotesk / neo-grotesk typeface.

Huge typography.

Some headings may occupy 50–80% of viewport width.

Use typography as a spatial element.

Typography may:

slide behind the 3D model

be partially occluded by the model

move at different depth speeds

reveal through masks

stretch slightly during transitions

respond subtly to scroll velocity

Maintain excellent readability.

Suggested tone:

LOKI
BONE

BUILT FOR
CHAOS.

CHEW.
ROLL.
DESTROY.
REPEAT.

LOKI APPROVED.

ONE TOY.
ZERO CHILL.

Do NOT add unsupported claims such as:
“indestructible”
“veterinarian approved”
“100% safe”
unless I explicitly provide evidence.

Do not treat these as conventional rectangular sections.

The whole website should feel like one continuous animated sequence.

SEQUENCE 0 — PRELOADER

Minimal black screen.

Small text:
LOADING LOKI...

Create a refined loading progress indicator tied to actual GLB loading progress.

No fake timer.

When ready:
brief light flash / exposure transition
then reveal the toy.

SEQUENCE 1 — HERO

100vh or slightly taller.

Near-black environment.

The red Loki Bone floats in the center of the viewport.

High quality studio lighting.

Start with the toy fairly large.

Slight slow idle rotation.

Very subtle floating motion.

Mouse movement should produce extremely restrained parallax.

Large background typography:

LOKI
BONE

The model should visually overlap the letters.

Do NOT place the 3D model inside a card.

It exists directly in the visual space of the page.

Small supporting copy:

A chew toy for a dog
with absolutely no chill.

Small scroll hint.

The opening frame should immediately look like a high-end product commercial.

SEQUENCE 2 — SCROLL TAKEOVER

Pin the scene.

As the user scrolls:

camera moves closer
toy rotates slowly
headline separates
background shifts slightly
lighting becomes more dramatic

The scroll should directly scrub the timeline.

No canned autoplay sequence.

The user controls cinematography with scrolling.

At approximately 40% through this sequence,
the toy rotates from hero perspective toward a clean lateral profile.

Text appears:

BUILT
FOR
CHAOS.

Use huge typography entering from alternating directions.

Model remains in front of some letters and behind others.

SEQUENCE 3 — MACRO DETAIL

Transition smoothly into an extreme close-up.

Camera should approach the rubber surface.

Show:

pebble texture

central nubs

spikes

molded shape

material roughness

Do NOT switch to an image.

The actual GLB should remain rendered.

Use high-quality directional/rim lighting so geometry detail becomes visible.

Add a very subtle depth-of-field effect if performance allows.

Text should be minimal:

TEXTURE.
TEETH.
TROUBLE.

or:

CHEW.
ROLL.
REPEAT.

Do not obscure the product.

SEQUENCE 4 — ROTATION / MECHANICAL MOMENT

Pull the camera back.

Rotate the toy approximately 180 degrees during the scroll.

Make this motion extremely smooth.

If the five central rings exist as separate meshes:

animate tiny independent rotational offsets for them.

Do NOT make them spin like wheels.

The movement should be physically restrained and premium.

If the rings are NOT separate:
animate only the complete model.

Use a sharp moving rim light during the rotation to reveal the silhouette.

Large text crosses the viewport while the product rotates.

SEQUENCE 5 — RED ROOM

Transition the entire visual environment from black to deep saturated red.

The toy can temporarily become darker through lighting contrast.

Add an enormous off-white:

LOKI

behind it.

Camera passes slightly underneath the model.

This sequence should feel different from the previous scene without loading a new page.

Use lighting and camera transformation rather than cheesy transitions.

SEQUENCE 6 — INTERACTIVE PRODUCT MOMENT

Temporarily stop scroll-driven camera animation.

Present the toy centered on a neutral dark environment.

Allow the user to drag horizontally to rotate it.

Restrict controls:
no crazy zoom
no free camera
no disorienting movement

It should feel like a luxury product viewer.

Add very small UI:

DRAG TO INSPECT

When scrolling resumes, smoothly reclaim control from the interactive viewer.

Do not cause camera jumps.

SEQUENCE 7 — LOKI MOMENT

Make this playful.

Text:

TESTED BY
LOKI*

Smaller:

*Test methodology:
biting the hell out of it.

Keep the joke subtle and visually premium.

The model can enter from below with a physically pleasing overshoot.

Do not turn this into a meme page.

SEQUENCE 8 — FINAL PRODUCT SHOT

Return to a beautiful studio render.

Off-white or very light warm-gray environment.

The red toy sits/floats centrally.

Large final line:

ONE TOY.
ZERO CHILL.

LOKI BONE

Small footer:

A concept product experience.

Optional button:

SPIN IT AGAIN

Clicking it performs one beautiful controlled 360° rotation.

The model must look excellent.

Spend serious effort on lighting.

Use:

Environment maps where appropriate
multiple area/directional lights where necessary
soft contact shadows
physically believable material response
tone mapping
correct color management
high quality antialiasing
subtle ambient occlusion if performant

Consider:
AccumulativeShadows
ContactShadows
Environment
Lightformer

Do not overuse Bloom.

Rubber should look like RUBBER.

It should not look:
metallic
wet
plastic chrome
glowing
translucent

If the imported material is poor, improve its PBR parameters carefully while preserving textures.

Suggested material direction:
metalness near 0
medium/high roughness
strong red base color
microdetail visible through lighting rather than fake noise overlays

Use shadows sparingly and intentionally.

Treat the camera like a commercial product camera.

Use cinematic focal lengths.

Avoid fisheye distortion.

Avoid extreme perspective.

Use a mixture of:

50mm style product shot
70–100mm macro feel
controlled close-ups

Camera movement should have:
weight
inertia
smooth easing
purpose

Never randomly orbit.

Never rotate solely because “3D website”.

Every camera move must reveal something.

Animation quality is more important than quantity.

Use GSAP timelines + ScrollTrigger.

Use scrubbed animation for the primary cinematic timeline.

Use ScrollTrigger pinning where appropriate.

Use velocity only for very subtle secondary effects.

No springy startup-template animations everywhere.

No excessive bouncing.

No random staggered cards.

No generic fade-up-on-scroll applied to every element.

Build several sophisticated animations instead of 100 mediocre ones.

Aim for the feeling of a continuous camera shot.

Use Lenis to create smooth scroll behavior.

Synchronize Lenis properly with GSAP ScrollTrigger.

Do not create competing requestAnimationFrame loops.

Scroll must remain responsive.

Do not make scrolling feel delayed or heavy.

Build the experience with layered composition.

Use a persistent WebGL canvas.

DOM typography and WebGL should exist in the same visual hierarchy.

Model should sometimes appear:
in front of typography
between text layers
behind selected elements

Use CSS stacking and transparent WebGL composition thoughtfully.

Do not simply put Canvas as a rectangular background.

The website should feel spatial.

Create a custom cursor on desktop.

It should remain subtle.

Possible states:

default dot
DRAG when hovering interactive model
VIEW when hovering product interaction

Buttons should have sophisticated magnetic or displacement-style hover behavior,
but remain usable.

Navigation should be extremely minimal.

Logo:
LOKI/

Top-right:
SOUND OFF/ON
(optional only if sound is implemented properly)

Do not add hamburger navigation unless actually necessary.

Only implement audio if it materially improves the experience.

If implemented:
audio must be OFF by default.

Possible extremely subtle sounds:
rubber impact
low sub hit during reveal
small texture/rubbing sound
transition whoosh

Never autoplay audio without consent.

This is extremely important.

The website should look expensive without actually destroying the GPU.

Target smooth 60 FPS on a modern desktop.

Implement adaptive quality.

Use:
devicePixelRatio cap
PerformanceMonitor
conditional postprocessing
texture compression where appropriate
GLTF optimization
lazy loading
Suspense
resource reuse

Do not allocate vectors/materials/geometries every frame.

Do not call React setState every frame.

Use refs and useFrame for high-frequency 3D updates.

Preload the GLB.

Inspect polygon count and texture resolution.

If the Hunyuan output is absurdly heavy:
create an optimized web version while retaining the source asset.

Use glTF Transform / Draco / Meshopt / texture compression where appropriate.

DO NOT visually destroy the model merely to chase a Lighthouse score.

Desktop should receive the full experience.

Mobile may receive a reduced quality version.

The mobile version must be intentionally designed.

Do not simply shrink desktop.

Maintain:
product visibility
clean typography
strong composition
stable scrolling

Reduce:
postprocessing
DPR
shadow samples
background effects

On very weak devices, allow a reduced WebGL mode.

Do not remove the 3D product entirely unless WebGL is genuinely unavailable.

Respect prefers-reduced-motion.

For reduced-motion users:
retain an elegant static 3D product presentation with minimal transitions.

Architect the project cleanly.

Suggested structure:

src/
components/
scenes/
shaders/
hooks/
lib/
styles/
App.tsx

Example conceptual components:

LokiScene
LokiModel
LightingRig
ScrollController
HeroTypography
ProductDetailSequence
InteractiveViewer
Loader
CustomCursor

Separate:
3D state
DOM
scroll animation
visual styling

Avoid a monolithic 1500-line App.tsx.

Use TypeScript properly.

No ignored TypeScript errors.

No console errors.

No broken asset requests.

No React warnings.

Clean up ScrollTriggers on unmount.

Do not attempt to implement everything blindly in one pass.

Work like a senior creative developer.

FIRST:

Inspect the repository.

Inspect the GLB.

Run the current project.

Understand model orientation and scale.

Establish the WebGL render.

Create a premium hero shot.

Only after the hero looks excellent, build the scroll timeline.

At each major stage, verify the site in the browser.

Pay attention to:
framing
lighting
camera clipping
responsive behavior
scroll timing
z-index
overflow
FPS
loading state

If a design decision looks generic, redo it.

The result should make someone ask:

“Wait, this is a website?”

The first screen should be visually impressive even without scrolling.

The 3D model must remain crisp and premium throughout the experience.

There should be at least 4 genuinely memorable visual moments.

There must be no obvious placeholder content.

There must be no generic stock illustrations.

There must be no generic AI gradients.

There must be no generic Bento grid.

There must be no pointless dashboard UI.

There must be no fake product statistics.

VISUAL QUALITY IS THE PRIMARY GOAL.

Interaction quality is second.

Copy is third.

When complete:

Ensure npm install works from scratch.

Ensure npm run dev works.

Ensure npm run build succeeds with zero errors.

Test desktop.

Test mobile.

Test direct page refresh.

Test GLB loading.

Test reduced motion.

Check browser console.

Provide a short README explaining:

architecture

3D asset location

how to replace the model

how to run

how to build

performance decisions

Do not stop at scaffolding.

Do not give me a mockup.

Do not merely explain how to build it.

BUILD THE COMPLETE WORKING WEBSITE.
