# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise Containment Heights for Zero CLS
**Learning:** In projects using `box-sizing: border-box`, refactoring CSS (like consolidating alert box padding) can subtly change element heights. Using "guestimated" `contain-intrinsic-size` values for `content-visibility: auto` leads to minor layout shifts.
**Action:** Always use a measurement script (like Playwright) to capture the exact rendered height of components at standard viewports (e.g., 1280px) and use the `auto [height]` syntax to ensure pixel-perfect stability.

## 2025-05-16 - Above-the-Fold Exemptions and Asynchronous Web Fonts
**Learning:** When using `content-visibility: auto` on all sections of a single-page app, applying it to above-the-fold content incurs unnecessary containment/layout computation overhead during the critical initial rendering path. Furthermore, synchronous font stylesheets act as the sole render-blocking external resource.
**Action:** Explicitly set `content-visibility: visible` on sections that reside within the initial viewport to maximize initial paint efficiency, and utilize asynchronous preloading for web fonts to remove all render-blocking CSS.
