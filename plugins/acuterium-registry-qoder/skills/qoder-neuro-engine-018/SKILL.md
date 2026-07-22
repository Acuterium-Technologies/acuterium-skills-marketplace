---
name: qoder-neuro-engine-018
description: "Track cognitive load on a 0.0–1.0 scale. When load > 0.7, automatically simplify the interface."
---

<!-- Acuterium registry: qoder |  | category= | thread= -->

# Neuro-Adaptive UI Engine

## Cognitive Load Model

Track cognitive load on a 0.0–1.0 scale. When load > 0.7, automatically simplify the interface.

```typescript
interface CognitiveLoadState {
  value: number;           // 0.0 (relaxed) to 1.0 (overloaded)
  source: 'simulated' | 'eeg' | 'face2feel';
  lastUpdated: Date;
}

// Simulation: random walk every 5 seconds (development/demo mode)
function simulateCognitiveLoad(setLoad: (v: number) => void) {
  let load = 0.4;
  setInterval(() => {
    load = Math.min(0.9, Math.max(0.1, load + (Math.random() - 0.5) * 0.2));
    setLoad(load);
  }, 5000);
}
```

## Auto-Simplification Rules

When `cognitiveLoad > 0.7` AND neuro-adaptive mode is ON:
- Reduce quick actions to first 2 items
- Collapse sidebar to icons only
- Increase font size by 1 step
- Reduce particle count by 50%
- Simplify message bubbles (remove metadata)

## Emotional Context on Messages

Every message carries emotional metadata:

```typescript
interface EmotionalContext {
  valence: number;      // -1.0 (negative) to 1.0 (positive)
  arousal: number;      // 0.0 (calm) to 1.0 (excited)
  cognitiveLoad: number; // 0.0 to 1.0
}

// User messages: valence 0.3, arousal 0.5, current load
// AI responses: valence 0.6, arousal 0.4, load * 0.8
```

Display neuro-context panel on messages when neuro-adaptive is active:
```css
.neuro-context {
  margin-top: 0.5rem; padding-top: 0.5rem;
  border-top: 1px solid rgba(255,255,255,0.1); font-size: 0.7rem;
}
.neuro-metric { display: flex; align-items: center; gap: 0.5rem; }
.metric-bar { flex: 1; height: 4px; background: rgba(255,255,255,0.1); border-radius: 2px; }
.metric-fill { height: 100%; background: linear-gradient(90deg, var(--color-primary), var(--color-accent-purple)); }
```

## Neuro-Adaptive Message Styling

Messages from the AI when neuro-adaptive is ON get a visual indicator:
```css
.message.neuro-adapted { border-left: 4px solid #A78BFA; }
```

## EEG Integration Hook (Muse Headset)

```typescript
interface EEGIntegration {
  connect(): Promise<void>;
  onBrainwaveData(data: { alpha: number; beta: number; theta: number; delta: number }): void;
  disconnect(): void;
}
// Map brainwave bands to cognitive load:
// load = (beta / (alpha + theta)) normalized to 0-1
```

## Face2Feel Emotion Detection

```typescript
interface Face2FeelConfig {
  consent: 'explicit' | 'implicit' | 'opt-out';
  model: 'tensorflow-affectnet'; // client-side, no server upload
  emotions: ['neutral', 'happy', 'sad', 'angry', 'fearful', 'disgusted', 'surprised'];
}
// Graceful fallback when camera unavailable or consent denied
// Results feed into PATHOS 5-axis emotion vector (QODER-COGNITIVE-ENGINES-004)
```

## Integration with Cognitive Engines

This engine feeds data into the ACAI V2 cognitive engine pipeline:
- NEXUS receives raw input signals → feeds cognitive load
- PATHOS receives emotional data → computes 5-axis emotion vector
- KAIROS receives combined state → decides interface mode switches

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY
- **Shard:** Marel | **Thread:** T13 — ACAI V2
- **Dependencies:** QODER-COGNITIVE-ENGINES-004, QODER-DESIGN-TOKENS-002
