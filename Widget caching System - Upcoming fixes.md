07.13.2026

## Refactoring
- Refactored the tab-switching logic in `SettingsRoot` to improve readability and maintainability.
- Moved the entire widget cache management system to `GameInstance`.
- Introduced the `BPI_WidgetStack` interface to remove direct references to `CommonActivatableWidgetStack`, preventing inactive widgets from remaining referenced after garbage collection.
- Moved `Canvas_Root` (containing the root `CommonActivatableWidgetStack`) from the `PlayerController` to the `PlayerHUD`.
- Replaced widget `Soft Class Reference` variables with a centralized `Primary Data Asset` solution, using Blueprint Interfaces for communication.
- Eliminated all hard references to core widgets. The Reference Viewer now contains only soft (pink) references.

## New Blueprint Interfaces

### `BPI_WidgetStack`
- `f_PushWidgetToLayer`
- `f_Release`

### `BPI_SettingsCommunicator`
- `f_CanvasSoftLink`

## Improved
- Fully removed hard references from the core UI architecture.
- Closing the pause menu now:
  - removes widgets from their parent;
  - clears the widget cache;
  - resets all cached widget variables.
- After garbage collection, the number of loaded widgets is reduced from approximately **400** to **60**.
- Removed the automatic `obj gc` call after widget deactivation to eliminate noticeable frame stutters.

## Investigated
- Identified an issue where reopening a widget after it has been removed from the cache - but before garbage collection occurs - creates a new instance instead of reusing or waiting for the previous one to be released.
- This can result in duplicate widget instances, increasing the total number of loaded widgets to over **1,200**.

## Planned Fixes
- Resolve the remaining widget caching and lifetime management issues.