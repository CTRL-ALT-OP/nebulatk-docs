# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

## `bounds_manager`

This module provides low-level functions for managing pixel-level hit detection and rectangular bounds for widgets, particularly useful for non-rectangular or transparent widgets.

---

### `generate_bounds_for_nonstandard_image(image, tolerance=0.75)`

Generates pixel-level bounds for a PIL image with transparency or irregular shapes.

|Parameter|Type|Description|
|---|---|---|
|`image`|`PIL.Image`|The image to generate bounds for.|
|`tolerance`|`float` (optional)|Minimum alpha (opacity) value (0–1) to include pixel in bounds. Default: 0.75.|

|Returns|Type|Description|
|---|---|---|
|`bounds`|`dict[int, list[list[int]]]`|Dictionary of horizontal scanlines with pixel ranges for visible areas.|

---

### `check_hit(_object, x, y)`

Performs hit-testing on a widget using its bounds or a pixel-perfect approximation for non-rectangular widgets.

|Parameter|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to check for a hit.|
|`x`|`int`|X coordinate (absolute).|
|`y`|`int`|Y coordinate (absolute).|

|Returns|Type|Description|
|---|---|---|
|`hit`|`bool`|`True` if the point is inside the widget's area.|

---

### `__OLD_remove_bounds(item, old_x, old_y, mode="box")`

**(Deprecated)** Removes a widget’s bounds from its master’s bounds tracking system.

|Parameter|Type|Description|
|---|---|---|
|`item`|`nebulatk.Widget`|The widget whose bounds should be removed.|
|`old_x`|`int`|The previous x position (relative).|
|`old_y`|`int`|The previous y position (relative).|
|`mode`|`str` (optional)|Either `"box"` or `"non-standard"`. Determines bound type. Default: `"box"`.|

---

### `__OLD_update_bounds(item, old_x, old_y, x, y, mode="box")`

**(Deprecated)** Updates the widget’s bounds in the master’s bounds map when the position changes.

|Parameter|Type|Description|
|---|---|---|
|`item`|`nebulatk.Widget`|The widget to update.|
|`old_x`|`int`|The old x position (relative).|
|`old_y`|`int`|The old y position (relative).|
|`x`|`int`|New x position.|
|`y`|`int`|New y position.|
|`mode`|`str` (optional)|`"box"` or `"non-standard"` mode for bounds. Default: `"box"`.|

> ⚠️ These `__OLD_*` functions appear to be deprecated or legacy internal functions and may be phased out.
