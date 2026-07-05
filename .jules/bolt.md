# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-20 - Placeholder Height and Padding Interaction
**Learning:** When using `content-visibility: auto`, the rendered placeholder height of an element equals the specified `contain-intrinsic-size` PLUS the element's total vertical padding. This remains true even if `box-sizing: border-box` is applied globally.
**Action:** When calculating `contain-intrinsic-size` for a target height, subtract the vertical padding from the measured total height to ensure zero CLS.
