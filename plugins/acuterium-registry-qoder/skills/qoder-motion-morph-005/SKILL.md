---
name: qoder-motion-morph-005
description: "Duration palette: Quick=base×0.5 | Standard=base | Slow=base×2.0 | Entrance=base×1.5 | Exit=base×0.75"
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# Motion, Morphing & CHRONOS Temporal System

## Motion Personality Tiers
| Tier | Base Duration | Easing | Default Edition |
|---|---|---|---|
| Premium | 300ms | cubic-bezier(0.22, 1, 0.36, 1) | Commercial |
| Judicial | 400ms | cubic-bezier(0.25, 0.1, 0.25, 1) | Government |
| Neutral | 350ms | cubic-bezier(0.4, 0, 0.2, 1) | Client |
| Energetic | 200ms | cubic-bezier(0.34, 1.56, 0.64, 1) | — |

Duration palette: Quick=base×0.5 | Standard=base | Slow=base×2.0 | Entrance=base×1.5 | Exit=base×0.75

## Glass Morphing Transitions
Shared-element morph (button→card→modal). Platform equivalents:
- **Web:** Framer Motion `layoutId` + `AnimatePresence`
- **iOS:** SwiftUI `@Namespace` + `glassEffectID` + `withAnimation`
- **Android:** Compose `sharedElement` + `rememberSharedContentState`

## Scroll Edge Effects
Glass fade at scroll boundaries:
- Web: `mask-image: linear-gradient(to bottom, transparent, black 20%)`
- iOS: `scrollView.topEdgeEffect`, `bottomEdgeEffect`
- Android: `drawWithContent` + gradient brush with `BlendMode.DstIn`

## CHRONOS Temporal System
**Government:** Prayer-time aware (Fajr/Duha/Dhuhr/Asr/Maghrib/Isha). Each phase shifts tint and particle behavior.
**Client:** Day/night auto-switch at 06:00/18:00.
**Rule:** CHRONOS transitions are ALWAYS slow tier (never abrupt).

## Aurora Particle System
30 (Gov) / 60 (Commercial) / 45 (Client). Colors from design tokens.
Physics: gentle drift, no sharp movements. Performance: max 2ms frame time.
Reduced motion: particles become static radial gradient.

## Breathing Orb
Idle: 4s cycle scale 1.0→1.1→1.0 | Processing: 1.5s | Active: 2s + color shift | Error: 0.8s + stress color.
Respects `prefers-reduced-motion`.

## Consciousness Bar
idle (thin, muted) → processing (expanding, accent cycling) → active (full, steady) → contemplating (pulsing, neuro color).
Smooth width and color interpolation.

## Anti-Patterns
- Never animate `backdrop-filter` directly (GPU-intensive); animate opacity
- Never use springs with high stiffness on glass elements
- Never loop particles/ambient animations in dashboard/data-heavy contexts
- Never skip `prefers-reduced-motion` check

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** Marel | **Thread:** T13
- **Dependencies:** QODER-DESIGN-TOKENS-002, QODER-GLASS-COMP-003
