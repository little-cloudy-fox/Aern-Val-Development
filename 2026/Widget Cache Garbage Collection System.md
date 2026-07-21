07.15.2026
## New Blueprint Function Library

### `BPF_CustomGC`
- Added `f_WidgetGC` for managing widget lifetime and cache cleanup.

## Refactoring
- Added the `WidgetCache` map variable to `GameInstance` to centralize widget cache management by unique widget IDs.
- Implemented `f_ProcessWGC` in `GameInstance`:
  - iterates through all cached widgets;
  - retrieves their individual cleanup timers;
  - checks whether the timer has expired;
  - releases expired widgets from the cache and marks them for garbage collection.

## Widget Lifetime Management
- Widget deactivation now triggers `f_WidgetGC`, which starts a **90-second cleanup timer**.
- After the timer expires, `f_ProcessWGC` is executed and removes unused widgets from the cache.
- If a widget is opened again before the timer expires:
  - the cleanup timer is cancelled;
  - the widget remains cached;
  - the cleanup process restarts only after the next deactivation.

### Planned Fixes
* Actor keeps duplicating and is not