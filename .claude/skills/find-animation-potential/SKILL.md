---
name: find-animation-potential
description: Audit a web page, screen or component for places where motion would make it clearer or more engaging, and return a ranked list of opportunities. Use when the user runs /find-animation-potential, or asks "where could this use animation", "what should move here", "make this page feel more alive" or similar. It finds and ranks; it does not implement unless the user then asks.
---

# Find animation potential

Find the places in a UI where motion earns its place: it explains something, gives feedback, guides attention or adds delight at a moment that matters. Report them ranked. Do not change code unless the user asks after seeing the list.

## 1. Pick the target

- If the user named a file, URL or component, use that.
- Otherwise use the page or screen most recently worked on in the conversation; failing that, the project's main entry page (index.html, the landing route, the app shell).
- Say in one line what you are auditing.

## 2. Take stock of existing motion

Search the target for `transition`, `animation`, `@keyframes`, `requestAnimationFrame`, `IntersectionObserver`, `animate(`, and motion libraries (Framer Motion, GSAP, Motion One, react-spring, Lottie). Note:

- what already moves, and how (duration, easing, trigger);
- whether `prefers-reduced-motion` is respected;
- anything that should **not** gain motion, e.g. an element that must stay faithful to a real product, dense data tables, or text people need to read while it loads.

If you can render the page (Playwright or a browser tool), screenshot it at desktop and phone width so judgments rest on what it looks like, not just the source.

## 3. Look for opportunities

Walk the page top to bottom and check each of these:

| Kind | Look for |
|---|---|
| **First impression** | A hero or first screen where nothing moves; headline or key visual could enter or idle gently. |
| **Explaining** | Steps, flows or how-it-works sections that could act out what they describe instead of only saying it. |
| **Feedback** | Buttons, copy-to-clipboard, forms, toggles and saves with no visible response; counters that change without a cue. |
| **State change** | Things that appear, disappear, expand, reorder or swap content instantly when a transition would show where they came from or went. |
| **Attention and progress** | Long pages or multi-step guides that could show progress (scroll-linked fills, active section in the nav). |
| **Hierarchy** | Groups that appear all at once where a short stagger would set reading order. |
| **Idle life** | Demos, previews or hero media that look static until clicked. |
| **Delight** | Wins, completions and calls to action where a small celebration fits the product. |
| **Problems** | Existing motion that is too slow (>500ms for UI feedback), uses linear easing for UI, animates layout properties (width, top, left) instead of transform and opacity, loops forever without reason, or ignores reduced motion. |

## 4. Judge each candidate

Keep a candidate only if you can say what the motion *does for the user*. For each, estimate:

- **Impact**: how visible the spot is and how much the motion helps (high / medium / low).
- **Effort**: rough size (a few lines of CSS, a small script, a larger build).
- **Risk**: performance, distraction, accessibility.

Rank by impact first, then effort. Drop anything that is motion for its own sake.

## 5. Report

Reply in this shape, short and plain:

1. **What you audited** – one line.
2. **Already animated** – a sentence or two, including whether reduced motion is respected.
3. **Opportunities** – a numbered list, best first. Each item: the element in bold, what would move and how (one or two sentences), and why it helps. Give a file and line reference when you have one.
4. **Leave alone** – anything that should not gain motion, and why.
5. **Recommendation** – the top 3–4 items you would build first, and offer to build them.

## Rules for any motion you later build

- Animate `transform` and `opacity`; avoid layout properties.
- UI feedback: 150–300ms. Entrances: 300–600ms. Ease-out (e.g. `cubic-bezier(.2,.7,.2,1)`) for things entering, ease-in for things leaving; never linear for UI.
- Stagger groups by 40–80ms per item, capped so the whole group finishes within about 600ms.
- Under `@media (prefers-reduced-motion: reduce)`, remove non-essential motion and keep the end state visible.
- Pause off-screen loops (IntersectionObserver) and avoid animating many elements every frame.
