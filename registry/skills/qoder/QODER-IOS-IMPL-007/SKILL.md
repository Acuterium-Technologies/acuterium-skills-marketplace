---
name: QODER-IOS-IMPL-007
description: "iOS/SwiftUI implementation of ACAI V2 — glass effects (.glassEffect, GlassEffectContainer), UIKit integration, WidgetKit modes, edition theming via EnvironmentValues, cognitive engine hooks, CHRONOS prayer-time adaptation. Targets iOS 26+. Use when building Acuterium iOS apps or glass-morphism mobile interfaces. Thread 13 — ACAI V2."
---

# iOS/SwiftUI Platform Implementation

## SwiftUI Glass Patterns
```swift
// Base glass
.glassEffect()
// Edition-aware
.glassEffect(.regular.tint(edition.accentColor).interactive())
// Button styles
.buttonStyle(.glass) / .buttonStyle(.glassProminent)
// Container
GlassEffectContainer(spacing: 12) { ... }
// Morphing
@Namespace var glassNS
.glassEffectID("card-1", in: glassNS)
withAnimation(.easeInOut(duration: 0.3)) { selectedID = "card-1" }
```

## Edition via EnvironmentValues
```swift
enum AcuteriumEdition { case government, commercial, client
  var accentColor: Color { ... }
  var headingFont: Font { ... }
  var particleCount: Int { ... }
}
struct AcuteriumEditionKey: EnvironmentKey { static let defaultValue: AcuteriumEdition = .commercial }
extension EnvironmentValues { var acuteriumEdition: AcuteriumEdition { ... } }
```

## UIKit Integration
`UIGlassEffect` with `UIVisualEffectView`, `UIGlassContainerEffect`, scroll edge effects via `scrollView.topEdgeEffect`.

## WidgetKit
Full color (default glass), Accented (`.widgetAccentable()`), Vignette (minimal glass hint). Edition-specific widget configs.

## CHRONOS
Prayer-time via `Calendar` + `CLLocationManager` for sunrise/sunset. Each phase adjusts tint and particle behavior.

## Accessibility
`accessibilityReduceTransparency` → opaque fallback. `accessibilityReduceMotion` → disable morphing. Dynamic Type support.

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** Marel | **Thread:** T13 | **Sovereignty Tier:** 3
