# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise Containment Heights for Zero CLS
**Learning:** In projects using `box-sizing: border-box`, refactoring CSS (like consolidating alert box padding) can subtly change element heights. Using "guestimated" `contain-intrinsic-size` values for `content-visibility: auto` leads to minor layout shifts.
**Action:** Always use a measurement script (like Playwright) to capture the exact rendered height of components at standard viewports (e.g., 1280px) and use the `auto [height]` syntax to ensure pixel-perfect stability.

## 2025-05-16 - Intrinsic Sizing in Border-Box Layouts
**Learning:** In a `box-sizing: border-box` layout, Chromium treats the `contain-intrinsic-size` hint as the *content-box* size and adds the element's padding on top when rendering the placeholder. If the hint is set to the *total* measured height, the placeholder becomes oversized by the amount of padding, causing Cumulative Layout Shift (CLS).
**Action:** Calculate `contain-intrinsic-size` as `(Total Rendered Height - Vertical Padding/Borders)` to achieve zero CLS.
