# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise Containment Heights for Zero CLS
**Learning:** In projects using `box-sizing: border-box`, refactoring CSS (like consolidating alert box padding) can subtly change element heights. Using "guestimated" `contain-intrinsic-size` values for `content-visibility: auto` leads to minor layout shifts.
**Action:** Always use a measurement script (like Playwright) to capture the exact rendered height of components at standard viewports (e.g., 1280px) and use the `auto [height]` syntax to ensure pixel-perfect stability.

## 2026-07-23 - Micro-Precise Google Font Intrinsic Sizing
**Learning:** External fonts loaded late (even with `font-display: swap`) can cause minor differences in block and line heights compared to system fallback fonts, leading to layout shifts when `content-visibility` placeholders render. Assigning semantic classes to all `<section>` tags and setting micro-precise `contain-intrinsic-size` heights matching the exact dimensions of Google Font 'Inter' at 1280px ensures absolute zero CLS.
**Action:** Ensure custom fonts are paired with exact measured heights for all deferred containers to achieve pixel-perfect layout stability.
