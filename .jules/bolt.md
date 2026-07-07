# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Accurate `contain-intrinsic-size` for CLS Prevention
**Learning:** When using `content-visibility: auto`, the `contain-intrinsic-size` placeholder must match the *total* rendered height of the element, including padding and borders (especially with `box-sizing: border-box`). Subtracting padding from the measured height for the intrinsic size hint causes the browser to reserve insufficient space, resulting in Cumulative Layout Shift (CLS) when the element scrolls into view.
**Action:** Use the full bounding box height for `contain-intrinsic-size` hints. Always verify layout stability with a scroll-based visual check.
