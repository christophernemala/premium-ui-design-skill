# Cinematic Motionography & Spring Physics Guidelines

Motion must feel premium, intentional, serene, and physically grounded. Never decorative noise.

## Core Principles
1. Communicate, don’t decorate.
2. Cinematic timing — deceleration and natural settle.
3. Physics over linear curves for interactive UI.
4. GPU-only properties (transform, opacity, filter, clip-path).
5. Honor prefers-reduced-motion.
6. Stagger with purpose (40–80 ms).

## Spring Physics Explained

A spring follows a damped harmonic oscillator. The parameters control how the system returns to equilibrium:

- **stiffness** (k) — Restoring force strength. Higher = snappier, more sudden movement. Typical UI: 100–500.
- **damping** — Opposing force that removes energy. Higher = less oscillation, faster settle. Typical: 15–40.
- **mass** — Inertia of the object. Higher = slower acceleration and more momentum. Keep ~1 for UI; raise for large cinematic objects.
- **bounce** (convenience API) — 0 = critically damped (no overshoot). 0.1–0.2 = subtle premium overshoot. >0.25 feels playful — avoid on serene/luxury work.
- **velocity** — Initial speed. Useful for gesture continuity.
- **restSpeed / restDelta** — When the animation is considered finished (prevents infinite tiny oscillations).

**Duration + bounce API** is preferred for predictable timing. Physics parameters give finer control over feel.

Recommended damping ratio for serene premium work: slightly under-damped to critically damped (almost no visible bounce, elegant settle).

### Ready-to-use Spring Presets (Framer Motion / Motion)

```ts
// Micro (buttons, icons, toggles) — immediate
{ type: "spring", stiffness: 400, damping: 30 }          // or bounce: 0.08

// Standard UI (cards, menus, list items)
{ type: "spring", duration: 0.28, bounce: 0.12 }

// Smooth / luxurious entrance (modals, large panels, hero elements)
{ type: "spring", stiffness: 120, damping: 20, mass: 1.05 }

// Cinematic heavy object
{ type: "spring", stiffness: 80, damping: 18, mass: 1.4 }

// Hover / tap feedback
{ type: "spring", stiffness: 400, damping: 17 }

// Layout / shared element
{ type: "spring", duration: 0.55, bounce: 0.1 }
```

## Recommended Durations
| Category                        | Duration    |
|---------------------------------|-------------|
| Micro (hover, focus, press)     | 100–200 ms  |
| Standard enter/exit             | 200–350 ms  |
| Complex / page / shared         | 350–550 ms  |
| Hero / cinematic ambient        | 600–1200 ms |

## Cinematic Patterns
- Staggered children with short delay
- whileInView once for scroll reveals
- Subtle y + opacity + scale for cards
- Pointer-driven tilt (max ±8–12°) with transformPerspective 800–1200
- Slow R3F camera moves (0.8–2 s) with damping
- Hybrid: Motion for canvas container entrance; useFrame / springs for internal 3D
- Film-grain + subtle vignette as final polish

## 3D & Shader Motion
- Prefer 21st.dev liquid-metal, glass, aurora, volumetric, and 3D-card components as base
- Internal object motion via useFrame or @react-spring/three
- Post-processing (bloom, grain, vignette) applied carefully — see threejs-shaders.md
- High-resolution 4K textures and product renders for motionographic quality

## Performance Checklist
- Transform + opacity only
- Pause ambient shaders off-screen
- Dispose R3F resources
- dpr ≤ 1.5
- Reduced-motion fallback that collapses to duration: 0 or simple fade

## Anti-patterns
- Linear timing on interactive elements
- Bounce > 0.2 on serene/luxury UI
- Layout-thrashing properties
- Infinite off-screen animations
- Competing motion that distracts from product clarity
- Over-bloom or heavy post-processing on mobile
