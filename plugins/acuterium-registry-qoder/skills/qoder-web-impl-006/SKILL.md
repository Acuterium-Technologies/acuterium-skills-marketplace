---
name: qoder-web-impl-006
description: "---"
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# Web/React Platform Implementation

## Tech Stack
React 18, TypeScript, Vite, Tailwind CSS, tRPC, Framer Motion, TensorFlow.js (Face2Feel), Lucide React icons.

## Project Structure
```
src/
  components/AUI/          # Glass components (GlassButton, GlassCard, etc.)
  components/Cognitive/    # ConsciousnessBar, BreathingOrb, AuroraParticles
  hooks/                   # useCognitiveState, useEdition, useChronos
  providers/               # EditionProvider, CognitiveProvider
  styles/tokens/           # Edition CSS files (gov.css, commercial.css, client.css)
  lib/                     # NEXUS, PATHOS, KAIROS, MNEMOS, TELOS engine classes
```

## Edition Provider
```tsx
const EditionContext = createContext<Edition>('commercial');
export const useEdition = () => useContext(EditionContext);
// Set data-edition attribute on :root for CSS token switching
```

## Tailwind Config Extension
Extend with Acuterium tokens: colors from `--acai-*`, fonts from `--acai-font-*`, radii from `--acai-radius-*`.

## Framer Motion Patterns
- Shared-element morph: `<motion.div layoutId="card-1">` with `AnimatePresence`
- Entrance: `initial={{ opacity: 0, y: 20 }} animate={{ opacity: 1, y: 0 }}`
- Consciousness bar: `useSpring` for width transitions between states

## Aurora Particles (Canvas)
Use `<canvas>` with `requestAnimationFrame`. Color palette from edition tokens. Cap at 2ms frame time. Clear with `globalCompositeOperation = 'lighter'` for glow effect.

## Bilingual RTL
```tsx
<div dir={locale === 'ar' ? 'rtl' : 'ltr'}>
// Use logical CSS properties: margin-inline-start, padding-inline-end
```
Arabic font: Noto Kufi Arabic (Government), IBM Plex Sans Arabic (fallback).

## Performance Checklist
- `will-change: transform` on glass elements (remove after animation)
- Lazy-load TensorFlow.js for Face2Feel
- Debounce NEXUS event listeners (mousemove: 16ms, scroll: 100ms)
- Use CSS containment: `contain: layout paint` on glass containers

## Browser Compatibility
- `backdrop-filter`: Chrome 76+, Safari 9+, Firefox 103+ (with `-webkit-` prefix)
- `@supports` fallback for older browsers

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** Marel | **Thread:** T13
- **Dependencies:** All design skills (001-005)
