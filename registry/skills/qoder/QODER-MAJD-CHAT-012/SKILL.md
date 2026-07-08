---
name: QODER-MAJD-CHAT-012
description: "MAJD chat interface pattern — bilingual Arabic/English chat UI with neuro-adaptive mode, cognitive load indicator, conversation history sidebar, quick actions grid, Framer Motion message animations, footer status bar (AI/Neuro/Quantum). Based on URANA's MajdChatInterface. Use when building AI chat interfaces with Acuterium's signature bilingual neuro-adaptive design. Thread 13 — ACAI V2."
---

# MAJD Chat Interface Pattern

## Layout Structure
Full-height flexbox: Header → Main (Sidebar + ChatArea) → Footer.

## Header
- Bilingual title: English gradient text (gold→purple) + Arabic gold text
- Subtitle: "Command the Edge of Intelligence" / Arabic equivalent
- Neuro-Adaptive toggle button (Brain icon, active glow)
- Cognitive Load indicator: label + progress bar + percentage

## Sidebar (280px)
- Conversation History with active indicator (gold left border)
- Quick Actions grid: Generate Report, Automate Task, Schedule Trend, Upload File
- Each action: icon + English label + Arabic label + accent-colored left border
- RTL: borders and transforms mirror

## Chat Area
- Messages: max-width 70%, rounded corners (user: bottom-right sharp, assistant: bottom-left sharp)
- User messages: gold gradient background. Assistant: purple gradient. System: blue-tinted glass.
- Framer Motion: `initial={{ opacity: 0, y: 20 }} animate={{ opacity: 1, y: 0 }}`
- Message header: sender icon + name + neuro indicator (Brain icon for neuro-adapted) + timestamp
- ArabicTypography component wraps all text for proper font rendering

## Input Area
- Glass input: `rgba(255,255,255,0.05)` bg, gold border at 30% opacity
- Focus: gold border + 3px gold ring shadow
- Bilingual placeholder: "Type your message here... / Arabic equivalent"
- Attach button (glass) + Send button (solid gold, black icon)
- Hint text below: Arabic suggestions + English suggestions

## Footer Status Bar
- Status dots: Online (green glow), Neuro-Adaptive (purple glow), Quantum (blue glow)
- Action buttons: Neuro Analysis, Quantum Insights, Auto-Optimize

## CSS Theme
Gold primary (#D4AF37), dark navy bg (#1a1f2e→#0a0f1a), purple accent (#8B5CF6).
Glass elements: `backdrop-filter: blur(10px)` on header, input container, footer.
Animations: `@keyframes pulse` (2s), `@keyframes shimmer` (3s gradient text).

## Accessibility
- `prefers-reduced-motion`: disable pulse/shimmer
- WCAG AA contrast on all text over glass backgrounds
- Keyboard navigation: Tab through actions, Enter to send

---

### APASF-SPEC-001 Appendix
- **Classification:** ACUTERIUM-PROPRIETARY | **Shard:** Marel | **Thread:** T13
- **Dependencies:** QODER-DESIGN-TOKENS-002, QODER-GLASS-COMP-003
