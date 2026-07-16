# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise Containment Heights for Zero CLS
**Learning:** When using `box-sizing: border-box` with `content-visibility: auto`, Chromium may treat the `contain-intrinsic-size` hint as the *content-box* size and then add padding/borders on top. This causes the placeholder to be larger than the rendered element, leading to Cumulative Layout Shift (CLS).
**Action:** Calculate the `contain-intrinsic-size` hint as `Natural Total Height - (Padding + Borders)`. Use Playwright to measure exact "natural" heights by forcing `content-visibility: visible` during measurement.
