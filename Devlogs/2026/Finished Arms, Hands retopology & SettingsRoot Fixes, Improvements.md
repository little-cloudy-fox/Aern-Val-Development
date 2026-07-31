07.31.2026

### Added
* Added confirmation popup window that shows up when Player tries to close settings with unsaved changes.
* `FPS_Limiter` slider now shows "Unlimited" value when it is at "0" value.

### Improved
* Improved "Restore Defaults" in `SettingsRoot`. It used to create another copy of `SettingsRoot` after deleting player's user settings slot. Now it works with cache.
* `SettingsRoot` was not caching properly: widget was removing from memory only when `CanvasRoot` was eliminated.
* Improved Color Grading on Scene.

### Upcoming
* Transitioning from custom MetaHuman characters to **fully custom-made models**.

### In progress
* Finish retopology.
* Texture character.
* Add hair cards for fur.
* Retarget character's skeleton to UE4 Mannequin.
* Add blendshapes (morph targets) for deep character customization.