---
name: QODER-DESIGN-TOKENS-002
description: "Acuterium design token system with three adaptive editions — Government (light #B8D4E8, Cinzel serif, Noto Kufi Arabic, prayer-time CHRONOS), Commercial (dark #0A0E1A, Inter sans-serif, gold #C9A84C, amber #FF6B35), and Client (auto-adaptive via CHRONOS temporal). Use when setting up theming, color palettes, typography, spacing, or switching between Acuterium editions. Thread 13 — ACAI V2."
---

# Design Tokens & Adaptive Theming

## Government Edition
```css
:root[data-edition="government"] {
  --acai-bg: #B8D4E8; --acai-bg-strong: #9BC4D8; --acai-bg-surface: rgba(155,196,216,0.85);
  --acai-fg: #1A2B3C; --acai-fg-muted: #3D5A73;
  --acai-accent: #4A7C9B; --acai-accent-hover: #3D6A86;
  --acai-stress: #D4A843; --acai-success: #2D8B5E;
  --acai-glass-bg: rgba(155,196,216,0.35); --acai-glass-border: rgba(74,124,155,0.25);
  --acai-glass-blur: 24px; --acai-glass-saturate: 1.6;
  --acai-font-heading: 'Cinzel', serif; --acai-font-body: 'Noto Kufi Arabic', 'Inter', sans-serif;
  --acai-particle-count: 30;
  --acai-radius-sm: 8px; --acai-radius-md: 16px; --acai-radius-lg: 24px; --acai-radius-pill: 999px;
  --acai-shadow-glass: 0 4px 24px rgba(26,43,60,0.08);
}
```

## Commercial Edition
```css
:root[data-edition="commercial"] {
  --acai-bg: #0A0E1A; --acai-bg-strong: #141926; --acai-bg-surface: rgba(20,25,38,0.85);
  --acai-fg: #E8ECF4; --acai-fg-muted: #8B95A8;
  --acai-accent: #C9A84C; --acai-accent-hover: #D4B85E; --acai-accent-secondary: #FF6B35;
  --acai-stress: #FF6B35; --acai-success: #10B981; --acai-neuro: #A78BFA; --acai-quantum: #60A5FA;
  --acai-glass-bg: rgba(20,25,38,0.65); --acai-glass-border: rgba(201,168,76,0.20);
  --acai-glass-blur: 32px; --acai-glass-saturate: 1.8;
  --acai-font-heading: 'Inter', sans-serif; --acai-font-body: 'Inter', sans-serif;
  --acai-particle-count: 60;
  --acai-radius-sm: 8px; --acai-radius-md: 16px; --acai-radius-lg: 24px; --acai-radius-pill: 999px;
  --acai-shadow-glass: 0 4px 24px rgba(0,0,0,0.25);
}
```

## Client Edition
```css
:root[data-edition="client"] {
  --acai-bg: #F0F2F5; --acai-bg-strong: #E2E5EB; --acai-fg: #1A1D26; --acai-fg-muted: #5A6070;
  --acai-accent: #5B7FFF; --acai-accent-hover: #4A6EE8; --acai-stress: #E85D3A;
  --acai-glass-bg: rgba(240,242,245,0.45); --acai-glass-border: rgba(91,127,255,0.15);
  --acai-glass-blur: 28px; --acai-glass-saturate: 1.6;
  --acai-font-heading: 'Inter', sans-serif; --acai-font-body: 'Inter', sans-serif;
  --acai-particle-count: 45;
}
@media (prefers-color-scheme: dark) {
  :root[data-edition="client"] {
    --acai-bg: #1A1D26; --acai-bg-strong: #252830; --acai-fg: #E8ECF4;
    --acai-glass-bg: rgba(26,29,38,0.55); --acai-glass-border: rgba(91,127,255,0.20);
  }
}
```

## Typography Scale
| Token | Size | Weight | Usage |
|---|---|---|---|
| `--acai-text-xs` | 0.75rem | 400 | Captions, timestamps |
| `--acai-text-sm` | 0.875rem | 500 | Sidebar, labels |
| `--acai-text-base` | 0.9375rem | 400 | Body, messages |
| `--acai-text-lg` | 1.125rem | 500 | Section headers |
| `--acai-text-xl` | 1.25rem | 600 | Arabic titles |
| `--acai-text-2xl` | 1.5rem | 700 | Page titles |
| `--acai-text-3xl` | 2rem | 700 | Hero headings |

## Spacing (4px Grid)
`--acai-space-1`: 4px | `--acai-space-2`: 8px | `--acai-space-3`: 12px | `--acai-space-4`: 16px | `--acai-space-6`: 24px | `--acai-space-8`: 32px | `--acai-space-12`: 48px

## CHRONOS Temporal Adaptation
**Government:** Fajr→Duha warm tint (+5% amber), Dhuhr→Asr neutral, Maghrib→Isha cool (+5% blue, -20% particles)
**Client:** 06:00-18:00 light, 18:00-06:00 dark. Transition: always slow tier (400ms+).

## RTL Support (Government)
Use logical properties: `margin-inline-start`, `padding-inline-end`. Mirror borders and directional indicators.

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** Marel | **Thread:** T13
- **Protocol Dependencies:** CHRONOS, ASIP v2 | **Sovereignty Tier:** 3
