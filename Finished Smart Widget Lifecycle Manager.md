07.17.2026
### Added
* Created a garbage collector actor class: `WidgetCleaner`.
* Refactored `BPF_CustomGC`.
* Created the `BPI_LGC` interface (`f_GetHandle`, `f_StartGC`) to retrieve `WidgetCleaner` instances and prevent duplicate instances.

### Improved
* Enhanced widget caching: All widgets are now cached, triggering `f_WidgetGC` on the `OnDestruct` event.
* Automated memory management: Inactive widgets are now automatically released from memory and cleared from the cache after 90 seconds.
### Investigated
* No issues found at this time.

### Upcoming / In Progress
* Migrate `WidgetCleaner` from an Actor class to a lightweight UObject-based class to strip out unnecessary replication and in-world features.
* Create a custom Blueprint Function Library (BPF) helper to simplify triggering and canceling the widget garbage collection process.

# ===== FINISHED WIDGET CACHING SYSTEM 🎉 =====