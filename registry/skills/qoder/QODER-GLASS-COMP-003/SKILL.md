---
name: QODER-GLASS-COMP-003
description: "Glassmorphism component library for Acuterium ACAI V2 — buttons, cards, containers, nav bars, toolbars, consciousness bar, breathing orb, aurora particles. Three edition variants. Cross-platform: CSS/React, SwiftUI, Jetpack Compose. Use when building glass UI components or applying frosted/blur effects. Thread 13 — ACAI V2."
---

# Glass Morphism Component Library

## Glass Base
```css
.glass {
  background: var(--acai-glass-bg);
  backdrop-filter: blur(var(--acai-glass-blur)) saturate(var(--acai-glass-saturate));
  -webkit-backdrop-filter: blur(var(--acai-glass-blur)) saturate(var(--acai-glass-saturate));
  border: 1px solid var(--acai-glass-border);
  border-radius: var(--acai-radius-md);
  box-shadow: var(--acai-shadow-glass);
}
@supports not (backdrop-filter: blur(1px)) {
  .glass { background: var(--acai-glass-bg-strong); }
}
```

## Components

**GlassButton:** `.btn-glass` default / `.btn-glass--prominent` solid accent. Hover: translateY(-2px). Active: scale(0.98). Focus: 3px ring.

**GlassCard:** Padding `--acai-space-6`, radius `--acai-radius-lg`. Gov: subtle inner glow. Commercial: gold border shimmer on hover.

**GlassContainer:** Groups elements in shared blur surface. `gap` = merge distance. Children lose individual glass background.

**GlassNavBar:** Fixed top, 64px, glass background. Scroll edge mask. Active item: accent underline + glow.

**GlassToolbar:** Horizontal action bar, glass treatment, icon buttons with glass hover.

**GlassInput:** `background: rgba(255,255,255,0.05)`, glass border, focus ring with accent color.

**GlassModal:** Overlay `rgba(0,0,0,0.5)` + blur(8px). Body: full glass. Entrance: scale 0.95→1 + fade.

**GlassChip:** Pill-shaped `--acai-radius-pill`, glass bg at 50%.

**GlassDivider:** 1px height, `--acai-glass-border`, optional accent glow.

## Signature ACAI V2 Components

### ConsciousnessBar
```css
.consciousness-bar { height: 3px; width: 100%; background: var(--acai-glass-border); position: relative; overflow: hidden; }
.consciousness-bar__fill { position: absolute; height: 100%; transition: width 0.4s ease, background 0.4s ease; }
/* States: idle=15% muted | processing=60% accent pulsing | active=100% accent | contemplating=40% neuro pulsing */
```

### BreathingOrb
```css
.breathing-orb { width: 12px; height: 12px; border-radius: 50%; background: var(--acai-accent); animation: breathe var(--orb-speed, 4s) ease-in-out infinite; }
@keyframes breathe { 0%,100% { transform: scale(1); opacity: 0.8; } 50% { transform: scale(1.15); opacity: 1; } }
/* Speeds: idle=4s, processing=1.5s, active=2s, error=0.8s with stress color */
```

### AuroraParticles
Canvas-based particle system. Colors pulled from edition tokens.
- Gov: 30 particles, slow drift, muted | Commercial: 60, gentle float, gold/purple | Client: 45, neutral blue
- Performance budget: max 2ms frame time
- Reduced motion: static radial gradient fallback

## Edition Switching
On edition change: glass-bg/border colors, blur radius (24/32/28px), particle count (30/60/45), font families, stress color all shift automatically via CSS custom properties.

## Accessibility
- Min 4.5:1 contrast for text on glass
- `prefers-reduced-transparency: reduce` → opaque backgrounds
- `prefers-reduced-motion: reduce` → disable breathe/pulse/particles
- Focus rings always visible
- `aria-label` describes glass state

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** Marel | **Thread:** T13
- **Dependencies:** QODER-DESIGN-TOKENS-002 | **Output:** `{ components[], edition, platform, accessibility{} }`
