# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precision Measurements for contain-intrinsic-size
**Learning:** When using `content-visibility: auto`, accurate `contain-intrinsic-size` hints are critical to prevent Cumulative Layout Shift (CLS). Simple bounding box measurements often fail if the element hasn't fully rendered or is affected by `box-sizing: border-box`. Using a Playwright script to perform a full-page scroll before measuring ensures all deferred content is rendered and dimensions are stable.
**Action:** Always use a scrolling measurement script to determine precise heights for `contain-intrinsic-size` hints.
