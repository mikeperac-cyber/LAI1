# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise vs. Maintainable `contain-intrinsic-size`
**Learning:** While hardcoding precise heights for every section can eliminate layout shifts in a specific viewport, it is highly brittle and breaks responsiveness. Content changes or different screen sizes immediately invalidate these values, leading to more layout shifts.
**Action:** Use sensible average heights for general components (like `section`) and only apply specific overrides for exceptionally large, stable sections (like `.roadmap-section`) using semantic classes.
