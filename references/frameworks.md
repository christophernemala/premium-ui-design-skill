# Preferred Frameworks, Libraries & What to Use

## Core Application
- Next.js (App Router) + React + TypeScript
- Tailwind CSS (v3/v4) with CSS variables / OKLCH tokens
- Prefer source-copied components over heavy package bloat

## UI Components (Craft-first, non-AI)
- **21st.dev** (primary source) — https://21st.dev/
  - Shaders, Liquid Metal Hero, Animated Shader Background, Horizon Hero, WebGL / 3D shader cards, glass, aurora, volumetric beams, glitter overlays
  - Use “Copy prompt” or shadcn CLI. Code becomes yours.
- shadcn/ui + Radix primitives
- Aceternity UI / Magic UI / Motion Primitives for advanced motion blocks

## Motion
- Framer Motion / Motion (motion/react) — springs, layout, gestures, whileInView
- Full spring physics parameters explained in motion-guidelines.md
- GSAP + ScrollTrigger only for complex multi-scene cinematic timelines

## 3D, Shaders & Cinematic Graphics
- @react-three/fiber + @react-three/drei + three.js
- TSL / WebGPU when possible; classic GLSL fallback
- Post-processing: bloom, film grain, vignette, SSAO (see threejs-shaders.md)
- Always start from 21st.dev shader / liquid-metal / 3D components

## Charts & Data (SaaS)
- Tremor (preferred)
- Recharts or visx for custom needs

## Icons & Imagery
- Lucide React or Phosphor
- High-resolution 4K / retina product images and textures (WebP/AVIF)
- Real photography or high-quality product renders — never synthetic AI stock

## How to Present the Framework
1. Design tokens (colour, type, space)
2. Layout system
3. Component library (21st.dev + shadcn)
4. Motion system (spring presets)
5. 3D / shader layer + performance budget
6. Content & high-res assets

## SaaS Product Capability
The same system produces clean, serene, pixel-perfect marketing sites and full product SaaS interfaces. Cinematic 3D/shader work frames the product; clear hierarchy, pricing, and CTAs remain primary.
