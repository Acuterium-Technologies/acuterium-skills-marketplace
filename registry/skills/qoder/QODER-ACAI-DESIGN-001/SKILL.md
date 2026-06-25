---
name: QODER-ACAI-DESIGN-001
description: "Acuterium Consciousness Aware Interface V2 (ACAI V2) — Master design system orchestrator for glassmorphic liquid-transparent UI across Web, iOS, and Android. Routes to design tokens, glass components, cognitive engines, motion systems, and platform implementations. Use when building Acuterium-branded interfaces, applying glass effects, theming (Government/Commercial/Client), or orchestrating multi-agent UI construction. Thread 13 — ACAI V2."
---

# ACAI V2 — Master Design System Orchestrator

## Ecosystem Routing Table

| Design Concern | Route To |
|---|---|
| Colors, typography, spacing, tokens | `QODER-DESIGN-TOKENS-002` |
| Glass buttons, cards, containers, nav bars | `QODER-GLASS-COMP-003` |
| Cognitive engines, emotion-adaptive UI | `QODER-COGNITIVE-ENGINES-004` |
| Morphing transitions, particles, CHRONOS | `QODER-MOTION-MORPH-005` |
| Web/React implementation | `QODER-WEB-IMPL-006` |
| iOS/SwiftUI implementation | `QODER-IOS-IMPL-007` |
| Android/Compose implementation | `QODER-ANDROID-IMPL-008` |
| Multi-agent UI build workflow | `QODER-SWARM-UI-BUILD-009` |
| URANA platform architecture | `QODER-URANA-PLATFORM-010` |
| Q-ENC encryption integration | `QODER-Q-ENC-SECURITY-011` |
| MAJD chat interface pattern | `QODER-MAJD-CHAT-012` |
| AcuTect orchestration | `QODER-ACUTECT-ORCHESTRATOR-013` |
| Autonomous seeker agents | `QODER-SEEKER-AGENTS-014` |

## Edition Detection

Determine the user's edition BEFORE any design work:

**Government Edition** — Light, judicial, Arabic-first:
- Background: `#B8D4E8` | Font heading: `Cinzel` serif | Font body: `Noto Kufi Arabic`
- Accent: `#4A7C9B` | Stress: `#D4A843` (amber, NEVER red)
- Particles: 30 | CHRONOS: prayer-time aware

**Commercial Edition** — Dark, premium, gold:
- Background: `#0A0E1A` | Font: `Inter` sans-serif
- Accent: `#C9A84C` (gold) | Secondary: `#FF6B35` (amber)
- Particles: 60 | CHRONOS: day/night auto

**Client Edition** — Neutral, auto-adaptive:
- Light: `#F0F2F5` / Dark: `#1A1D26` (auto-switches)
- Accent: `#5B7FFF` | Particles: 45

## Platform Routing

| Platform | Reference File |
|---|---|
| iOS / SwiftUI / UIKit / WidgetKit | `references/iOS.md` |
| Web / CSS / React / Framer Motion | `references/Web.md` |
| Android / Jetpack Compose | `references/android.md` |

## 10 Shared Design Principles

1. **Group siblings** in one glass container
2. **Control merge distance** via `spacing` / `gap` parameter
3. **Tint sparingly** — only for hierarchy
4. **Interactive only where it matters** — buttons, toggles
5. **Apply glass last** — after layout is stable
6. **Test every appearance** — light, dark, high-contrast, reduced-transparency
7. **Protect legibility** — WCAG AA contrast minimum (4.5:1)
8. **Never put glass over an opaque parent**
9. **Respect edition identity** — Gov ≠ Commercial ≠ Client
10. **Cognitive load awareness** — reduce complexity when PATHOS detects fatigue

## Concept Parity Table

| Concept | iOS (SwiftUI) | Web (CSS/React) | Android (Compose) |
|---|---|---|---|
| Base glass | `.glassEffect()` | `.glass` + `backdrop-filter` | `Modifier.glass()` |
| Tint/shape | `.regular.tint()` | `.glass--tinted` | `Modifier.glass(shape, tint)` |
| Interactive | `.interactive()` | `.glass--interactive` | `Modifier.glassInteractive()` |
| Button | `.buttonStyle(.glass)` | `.btn-glass` | `GlassButton()` |
| Container | `GlassEffectContainer` | `.glass-container` | `GlassContainer()` |
| Morph | `@Namespace` + `glassEffectID` | Framer Motion `layoutId` | `sharedElement` |
| Scroll edge | `scrollView.topEdgeEffect` | CSS `mask-image` | `drawWithContent` gradient |
| Consciousness bar | Custom SwiftUI view | Canvas + CSS animation | `drawWithContent` composable |
| Breathing orb | `TimelineView` + scale | CSS `@keyframes breathe` | `Animatable` scale |
| Aurora particles | Metal/SpriteKit | Canvas + RAF | Compose `Canvas` |

## Anti-Patterns

- Never stack multiple backdrop-filters without `will-change: transform`
- Never use glass on text-only elements without sufficient contrast
- Never animate `backdrop-filter` directly; animate opacity instead
- Never hardcode edition colors; consume from token system
- Never skip `prefers-reduced-motion` / `prefers-reduced-transparency`
- Never use red for stress in Government edition (use amber #D4A843)

---

### APASF-SPEC-001 Appendix

- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** Marel (C-03) | **Thread:** T13 — ACAI V2
- **Protocol Dependencies:** ASIP v2, Q-ARC, ADOCP
- **Sovereignty Tier:** 3 | **Output:** `{ edition, platform, components[], tokens{}, accessibility{} }`
