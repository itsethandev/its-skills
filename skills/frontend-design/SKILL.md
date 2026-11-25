---
name: frontend-design
description: Design frontend pages, components, and interactive prototypes, or change an existing UI's layout, styling, or interactions. Build task-centered layouts with concise copy, familiar icons, and deliberate visual hierarchy.
---

# Frontend Design

Design around the user's task, not the implementation. Preserve accepted scope and behavior; ask about consequential product decisions rather than inventing answers.

Follow user direction, then intentional project conventions and accepted decisions, then these defaults. Establish conventions from design guidance or configured components, not incidental styling. Preserve compatible usability and accessibility rules.

## Plan the screen

1. Read the brief, real content, and UI conventions. Identify the audience, main task, and primary action. Ask only about gaps that materially affect behavior or design.
2. Separate essential content, guidance needed on demand, and content to omit. Keep what users need to act or understand the outcome; add no filler sections.
3. Before coding, plan information order, grouping, actions, spacing, type hierarchy, color roles, and narrow-screen behavior. Reuse suitable tokens and components; sketch alternatives when useful. Scale the plan to the change and proceed within existing authority without a routine approval pause.

## Build with restraint

- Make the primary action obvious. Group related content through proximity, alignment, and spacing before adding containers or explanations.
- Match type, palette, density, and imagery to the audience and subject. Extend an existing visual language; for new UI, choose a coherent direction rather than generic decoration.
- Emphasize important content and quiet its surroundings. Borders, cards, dividers, and motion must communicate grouping, priority, state, or useful feedback.
- Preserve useful density and essential controls; avoid excessive whitespace that separates related information.
- Cover relevant validation, loading, success, failure, and empty states. Place feedback where the user acted; preserve recovery paths and required disclosures.

### Make text earn its place

Use short, specific labels in the user's vocabulary. Name the action, not its implementation, consistently throughout the flow.

Remove introductions that repeat headings, obvious-control explanations, and notices about implementation conveniences. Routine draft persistence needs no storage explanation; explain consequences for privacy, retention, or user decisions instead.

Place secondary guidance near its field or reveal it on demand. Preserve information needed before acting, explicit field labels rather than placeholders alone, and useful error and recovery instructions.

### Use icons intentionally

Use familiar icons when context makes the action clear; retain short labels for ambiguous actions or destinations. Avoid decorative icons on every label.

Use the project's icon set, falling back to Lucide within the authorized toolchain. Reuse suitable options before adding dependencies. Keep size, stroke, alignment, and hit areas consistent. Give icon-only controls accessible names, visible keyboard focus, and adequate pointer targets; hide decorative icons from assistive technology. Tooltips may supplement controls, but cannot be their only accessible name or the only way to discover an unfamiliar action.

### Keep prototype commentary out of the UI

Omit preview banners, demo disclaimers, technical notes, and unfinished-feature lists unless requested or required by accepted product constraints. Put limitations in the handoff or developer documentation.

Keep interaction-local feedback truthful: simulated actions must not imply real payments, deliveries, or submissions. This does not require a global disclaimer.

## Inspect and simplify

Render at desktop and mobile sizes with available, authorized browser tools and inspect screenshots; compilation does not establish visual quality. Exercise the primary interaction and relevant failure states. Check hierarchy, spacing, wrapping, overflow, keyboard navigation, contrast, focus, and reduced-motion behavior when motion is present. Narrow layouts must preserve the task, not merely shrink the desktop layout.

After inspection, remove text, containers, and decoration that add no meaning; preserve essential labels, consequences, and recovery guidance. Correct clutter and interaction problems within scope, then inspect the affected result again.

Finish when the primary task is clear and usable, explanations serve user needs, and checks pass or have specific reported limits. Without rendering tools, run supported source checks and report visual and interaction quality as unverified.
