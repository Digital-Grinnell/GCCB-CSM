# Timeline page behavior (native vs TimelineJS)

This project supports two timeline experiences:

- Native CollectionBuilder timeline page at /timeline.html
- Knight Lab TimelineJS page at /timelinejs.html

## Expected page wiring

Native timeline page should use this pattern in pages/timeline.md:

```yaml
---
title: Timeline
layout: timeline
permalink: /timeline.html
---

##
Collection Timeline
```

Standalone TimelineJS page should use this pattern in pages/timelinejs.md:

```yaml
---
title: TimelineJS
layout: page-full-width
permalink: /timelinejs.html
---

{% include feature/timelinejs.html %}
```

## Known regression and fix (2026-07-01)

A regression changed pages/timeline.md to page-full-width and embedded feature/timelinejs.html.
That made both navigation links render TimelineJS instead of having one native timeline and one TimelineJS page.

Fix:

- Restore pages/timeline.md to layout: timeline
- Remove TimelineJS embed from pages/timeline.md
- Keep pages/timelinejs.md as the TimelineJS page

## Navigation note

The Timelines dropdown in _data/config-nav.csv is valid and can include both links:

- Full Timeline -> /timeline.html
- TimelineJS -> /timelinejs.html

The dropdown is only a menu structure. Actual behavior depends on each page file's layout and content.
