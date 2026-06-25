# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Granular Content Visibility for Roadmap Items
**Learning:** While applying `content-visibility: auto` to large sections is beneficial, applying it to granular, repetitive items (like individual roadmap days) within those sections provides even better rendering performance. It allows the browser to manage much smaller chunks of the DOM, further reducing the work needed when only a few items are on screen.
**Action:** Identify repetitive list-like elements in long documents and apply `content-visibility: auto` with measured `contain-intrinsic-size` directly to those elements.
