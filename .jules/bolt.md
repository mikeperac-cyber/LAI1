# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2026-07-09 - High-Precision `contain-intrinsic-size` for CLS Prevention
**Learning:** In documents using `box-sizing: border-box`, `contain-intrinsic-size` hints must exactly match the total rendered height (including padding/borders). Even small discrepancies (15-40px) cause visible Cumulative Layout Shift (CLS) as elements enter the viewport. Precise measurements via automated scripts (e.g., Playwright) are necessary for accuracy.
**Action:** Always use Playwright to measure total element height in the target viewport before setting `contain-intrinsic-size` values. Use semantic classes (e.g., `.roadmap-section`) for specific large-element hints to ensure maintainability.
