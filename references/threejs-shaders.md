# Three.js / R3F Shader Effects & Cinematic Pipeline

## Preferred Stack for Cinematic 3D Websites
- React Three Fiber + @react-three/drei
- three.js (latest)
- Prefer TSL (Three.js Shading Language) + WebGPU when targeting modern browsers; fall back to classic GLSL + WebGL
- Post-processing via EffectComposer (legacy) or RenderPipeline / TSL nodes (modern)
- Always source starting points from 21st.dev shader / liquid-metal / 3D-card components before writing custom GLSL

## High-Value Shader Effects for Premium / SaaS / Cinematic Sites

| Effect | Use Case | Notes |
|--------|----------|-------|
| Liquid Metal / Iridescent | Hero product, logo, CTA cards | Fresnel + noise + environment mapping. 21st.dev has strong examples |
| Glass / Transmission | Soft glass panels, floating UI | MeshPhysicalMaterial transmission + thickness + roughness. Soft glass with compute shaders for higher quality |
| Aurora / Volumetric Light | Background atmosphere | Raymarching or layered noise + glow. Keep lightweight |
| Film Grain + Vignette | Cinematic polish | Cheap single-pass; apply last. Strength 0.1–0.3 |
| UnrealBloom / Bloom | Soft glow on bright accents | Threshold carefully; never over-bloom |
| SSAO | Subtle contact shadows | Adds depth without heavy geometry |
| Chromatic Aberration | Subtle lens feel on transitions | Very low intensity |
| Domain Warping / FBM Noise | Organic backgrounds, liquid surfaces | Simplex / Perlin + domain warp |
| Fresnel Rim | Edge glow on 3D objects | Classic for premium product shots |
| Matcap / Custom PBR | Fast stylized materials | Useful for performance |

## Recommended Post-Processing Order
1. Scene render (with depth/normals if needed)
2. SSAO (if used)
3. Bloom
4. Colour grade / LUT / tint
5. Film grain + vignette
6. Anti-aliasing (FXAA / SMAA last)
7. Output / tone mapping

## Performance Rules for 3D SaaS Sites
- dpr={[1, 1.5]} on Canvas
- Dispose geometries, materials, textures on unmount
- Use InstancedMesh / BatchedMesh for repeated objects
- LOD for complex models
- Pause off-screen scenes (selective rendering)
- Prefer 21st.dev pre-tuned shaders over raw unoptimized GLSL
- Mobile: disable heavy post-processing, reduce particle counts, lower dpr

## Integration with Motion
- Framer Motion / Motion for DOM entrance, layout, and canvas container animation
- useFrame + direct mutation or @react-spring/three for internal 3D object motion
- Never drive heavy R3F objects with Framer Motion springs every frame

## High-Resolution Imagery
- Use 4K (or retina) source images for textures and backgrounds
- Compress intelligently (WebP / AVIF) while preserving detail
- For product showcases, prefer high-quality .glb / .gltf with PBR maps over low-poly
- Pair with subtle parallax or shader distortion for motionographic feel
