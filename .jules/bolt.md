# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise Measurement for Content Visibility
**Learning:** When measuring element heights for `contain-intrinsic-size`, it is critical to use a fixed viewport and trigger a full-page scroll before measurement. `content-visibility: auto` elements may have different placeholder heights until they are scrolled into view and fully rendered, and their layout might affect surrounding elements (like the footer).
**Action:** Always use a Playwright script with a set viewport (e.g., 1280x800) and `window.scrollTo(0, document.body.scrollHeight)` to ensure stable layout before measuring dimensions for intrinsic size hints.
