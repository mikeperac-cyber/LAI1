# Bolt's Journal - Critical Learnings Only

## 2025-05-14 - Optimizing Long Static Roadmaps
**Learning:** For long, section-heavy static pages like roadmaps, `content-visibility: auto` provides a significant boost to initial rendering performance by deferring the layout and painting of off-screen sections. Using `contain-intrinsic-size` prevents layout shifts during scrolling. Additionally, `dns-prefetch` for external resource domains and a data-URI favicon (`data:,`) are simple but effective ways to reduce latency and redundant requests.
**Action:** Apply `content-visibility: auto` to major container elements in long documents. Proactively include resource hints for known external dependencies.

## 2025-05-15 - Precise Containment Heights for Zero CLS
**Learning:** In projects using `box-sizing: border-box`, refactoring CSS (like consolidating alert box padding) can subtly change element heights. Using "guestimated" `contain-intrinsic-size` values for `content-visibility: auto` leads to minor layout shifts.
**Action:** Always use a measurement script (like Playwright) to capture the exact rendered height of components at standard viewports (e.g., 1280px) and use the `auto [height]` syntax to ensure pixel-perfect stability.

## 2026-07-25 - Preloading Google Fonts from CDN as an Anti-Pattern
**Learning:** Hardcoding and preloading specific font file URLs directly from the Google Fonts CDN (e.g. `fonts.gstatic.com/.../hash.woff2`) is a major performance anti-pattern. Google frequently updates font files and their associated URL hashes. When they do, the `<link rel="preload">` will double-download an old unused font file while the browser downloads the updated font from the CSS file, wasting bandwidth and triggering browser console warnings.
**Action:** For CDN-hosted web fonts, rely on optimal `<link rel="preconnect">` and `font-display: swap` headers instead of preloading, unless self-hosting the font files locally where the URLs are fully controlled and stable.
