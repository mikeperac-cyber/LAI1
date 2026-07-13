# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise Containment Heights for Zero CLS
**Learning:** In projects using `box-sizing: border-box`, refactoring CSS (like consolidating alert box padding) can subtly change element heights. Using "guestimated" `contain-intrinsic-size` values for `content-visibility: auto` leads to minor layout shifts.
**Action:** Always use a measurement script (like Playwright) to capture the exact rendered height of components at standard viewports (e.g., 1280px) and use the `auto [height]` syntax to ensure pixel-perfect stability.

## 2025-05-16 - Box-Sizing and Content-Visibility Placeholders
**Learning:** In a `box-sizing: border-box` environment, Chromium (as of version 131) appears to apply padding *on top* of the `contain-intrinsic-size` height hint for elements with `content-visibility: auto`. This means that if you set the hint to the total natural height, the placeholder will be too large (Natural Height + Padding).
**Action:** When calculating `contain-intrinsic-size` for elements with significant padding, subtract the padding from the natural total height to ensure the placeholder size matches the final rendered height, effectively eliminating Cumulative Layout Shift (CLS).
