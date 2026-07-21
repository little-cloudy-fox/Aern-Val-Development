07.12.2026
### Added
- Added an additional dragon image to the `SettingsRoot` widget. Both dragon images are now selected randomly when the widget is created / activated.
- Implemented an interpolated parallax effect for:
  - dragon artwork;
  - section headers;
  - descriptions;
  - settings tabs.
- Added a fade-out animation for all `SettingsRoot` components (excluding tabs and navigation buttons) when the cursor moves toward the right side of the screen.

### Fixed / Investigated
- Investigated issues with the widget caching system:
  - Cached widgets are still being recreated in memory after closing and reopening them.
  - Widgets from the pause menu are not being fully released from memory after closing the menu, even after running `obj gc`. Some references to these widgets remain active (~470-610).

### Planned Fixes
- Prioritize fixing the widget caching system.

### Planned Improvements
- Expand the parallax effect to other widgets.
- Add an option to disable parallax effects for individual widgets.