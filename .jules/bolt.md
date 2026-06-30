# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2026-06-30 - Granular Content Visibility for Long Lists
**Learning:** On extremely long static pages (e.g., 7500px+), applying `content-visibility: auto` only to large sections may not be enough for optimal performance. Applying it to individual repetitive items (like list entries or cards) allows the browser to more precisely skip rendering work. Measuring the average height of these elements with a script is crucial for setting an accurate `contain-intrinsic-size` and avoiding layout shifts.
**Action:** Use granular `content-visibility` on repetitive items in very long documents. Always measure element dimensions to provide accurate size hints.
