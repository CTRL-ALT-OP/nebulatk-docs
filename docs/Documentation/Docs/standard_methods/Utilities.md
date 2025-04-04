# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

## `standard_methods.py`

The `standard_methods` module provides core utility functions for the `nebulatk` UI system. These include geometric calculations, positioning helpers, drawing logic, and standard behaviors for user interactions such as hover and toggle states.

---

### 📦 Constants

|Name|Description|
|---|---|
|`IMAGE_OBJECTS`|List of image-related object attribute names|
|`BG_OBJECTS`|List of background rectangle object names|
|`TEXT_OBJECTS`|List of text-related object names|
|`SLIDER_OBJECTS`|Reserved list for slider object names (not yet in use)|
|`ALL_OBJECTS`|Combined list of all known drawable widget object names|

---

### 🧮 Math Utilities

#### `clamp(number, minimum=0, maximum=0)`

Constrains a number to lie between a minimum and maximum.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`number`|`int`|The number to clamp|No|
|`minimum`|`int`|Lower bound|Yes (default `0`)|
|`maximum`|`int`|Upper bound|Yes (default `0`)|

**Returns:** `int` — The clamped value.

---

#### `sign(x)`

Returns the sign of a number.

|Argument|Type|Description|
|---|---|---|
|`x`|`int`|Input number|

**Returns:** `int` — `1` if `x >= 0`, `-1` if `x < 0`.

---

### 📐 Coordinate Transformations

#### `rel_position_to_abs(_object, x, y)`

Converts a position relative to a widget to an absolute screen position, walking up the parent hierarchy.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The reference widget|
|`x`, `y`|`int`|Relative position|

**Returns:** `(int, int)` — Absolute position.

---

#### `abs_position_to_rel(_object, x, y)`

Converts an absolute position to a position relative to a widget.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The reference widget|
|`x`, `y`|`int`|Absolute position|

**Returns:** `(int, int)` — Relative position.

---

### 🔺 Geometry Utilities

#### `get_line_point_rel(angle, length)`

Calculates the `(x, y)` vector for a line given an angle (radians) and length.

|Argument|Type|Description|
|---|---|---|
|`angle`|`float`|Angle in radians|
|`length`|`float`|Length of the vector|

**Returns:** `(float, float)` — Relative vector components.

---

#### `offset_point(a, _a, _b)`

Offsets a point `a` by components `_a`, `_b`.

|Argument|Type|Description|
|---|---|---|
|`a`|`tuple`|Starting `(x, y)` point|
|`_a`|`float`|Vertical offset|
|`_b`|`float`|Horizontal offset|

**Returns:** `(float, float)` — Offset point.

---

#### `normalize_angle(angle)`

Normalizes an angle to the range `[0, 360)` degrees.

|Argument|Type|Description|
|---|---|---|
|`angle`|`float`|Angle in degrees|

**Returns:** `float` — Normalized angle.

### ◼️ Rectangle Geometry Utilities

#### `get_rect_points(_object)`

Calculates the four corner points of a rotated rectangle widget.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget whose corners should be calculated|

**Returns:** `tuple[tuple[int, int], ...]` — Four `(x, y)` coordinates: `a` (top-left), `b` (top-right), `c` (bottom-right), `d` (bottom-left)

This function respects the widget's rotation angle (`_object.orientation`) and walks up the parent tree to get an absolute position.

---

#### `get_rel_point_rect(_object, x, y)`

Given an absolute point `(x, y)`, computes its relative position inside a rotated widget's bounding box.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget being evaluated|
|`x`, `y`|`int`|Absolute coordinates to convert|

**Returns:** `tuple[int, int]` — Relative coordinates `(rx, ry)` with respect to the rotated widget

---

#### `get_rect_area(_object)`

Calculates the area of a rectangular widget. Ignores rotation.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget whose area is needed|

**Returns:** `int` — Area (`width × height`)

---

#### `get_triangle_area(a, b, c)`

Calculates the area of a triangle given its three vertices using the shoelace formula.

|Argument|Type|Description|
|---|---|---|
|`a, b, c`|`tuple[int, int]`|The triangle vertices|

**Returns:** `float` — Area of the triangle

### ◼️ Flop Utilities

#### `image_flop(_object, val)`

Shows one specific image element on a widget, hiding all others in the `IMAGE_OBJECTS` list.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget instance|
|`val`|`str`|Name of the image attribute to make visible|

This is typically used to manage button image states like normal, hover, active, etc.

---

#### `bg_flop(_object, val)`

Shows one background rectangle and hides all others in the `BG_OBJECTS` list.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget whose background state to update|
|`val`|`str`|Background object attribute to make visible|

---

#### `text_flop(_object, val)`

Shows one text object and hides all others in the `TEXT_OBJECTS` list.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to update|
|`val`|`str`|Text object attribute to make visible|

---

#### `flop_off(_object)`

Hides all known visual elements on the widget. This includes text, background, and image elements.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to hide visuals from|

---

#### `flop_on(_object)`

Shows the correct combination of widget visuals based on the current widget state (`hovering`, `state`, etc.).

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to restore visuals for|

Automatically handles hover/active combinations for all image, background, and text objects.

### ◼️ Widget Deletion and Scheduling

These methods handle the removal of widget visuals from the canvas, both immediately and in a delayed manner.

---

#### `delete(_object, delayed=False)`

Deletes all visible elements (images, backgrounds, text) associated with a widget.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget whose objects will be deleted|
|`delayed`|`bool` _(optional)_|If `True`, objects are added to a deletion queue instead of being removed immediately|

If `delayed` is `True`, this will only delete objects previously queued with `schedule_delete()`.

---

#### `schedule_delete(_object)`

Queues all current visible widget elements for delayed deletion.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget whose objects will be marked for future deletion|

This allows you to safely remove a widget later, useful in animations or staged destruction flows.

---

#### `delete_scheduled(_object)`

Deletes all widget elements that were scheduled using `schedule_delete()`.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to finalize deletion on|

This is commonly called after the widget is no longer needed or should be fully cleared from the canvas.

### ◼️ Hover Behavior Utilities

These methods control the appearance and interactivity of widgets when hovered by the mouse. They handle visual changes like showing hover images, changing text or background states, and restoring visuals when the cursor leaves.

---

#### `hovered_standard(_object)`

Applies hover behavior for **standard widgets** by showing hover images and text/background if available.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to apply hover effects to|

If the widget has `hover_object`, `bg_object_active`, or `active_text_object`, they are displayed.

---

#### `hovered_toggle(_object)`

Applies hover behavior for **toggle widgets**, respecting their current toggle state.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The toggle-style widget to update|

Displays either `hover_object_active` or `hover_object` depending on the current toggle state.

---

#### `hover_end(_object)`

Restores the default (non-hover) state when the cursor leaves the widget.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to revert hover effects on|

Displays either `image_object` or `active_object` based on the toggle state, and shows default text/backgrounds.

### ◼️ Toggle Behavior Utilities

These functions define how widgets behave when their toggle state changes. They handle switching images, backgrounds, and text based on whether a widget is "on" or "off" (toggled).

---

#### `toggle_object_standard(_object)`

Toggles the state of a **standard widget**, flipping its active state and updating its image accordingly.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget to toggle|

- If `hovering` is `True`, sets the image to `hover_object_active`.
    
- Otherwise, sets the image to `active_object`.
    

---

#### `toggle_object_toggle(_object)`

Toggles the state of a **toggle widget**, updating its visual state and calling optional callbacks.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The toggle-style widget to toggle|

Behavior:

- If `hovering` is `True`, shows `hover_object_active`.
    
- Otherwise shows `active_object`, `hover_object`, or `image_object` depending on state.
    
- Also updates `bg_object_active` and `active_text_object` appropriately.
    
- Calls:
    
    - `command()` if toggled on.
        
    - `command_off()` if toggled off (if defined), otherwise falls back to `command()`.
        

### ◼️ Click Behavior Utilities

These functions define how widgets respond when clicked. They control toggling behavior and optional callback execution.

---

#### `clicked_standard(_object)`

Handles **click behavior** for **standard widgets**. Toggles state and calls a user-defined callback.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget being clicked|

Behavior:

- If the widget is visible:
    
    - Calls `toggle_object_standard()` to flip the state.
        
    - Executes `command()` if it is not `None`.
        

---

#### `clicked_toggle(_object)`

Handles **click behavior** for **toggle widgets**. Toggles state and calls the appropriate user-defined callbacks depending on the result.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The toggle-style widget clicked|

Behavior:

- If the widget is visible:
    
    - Calls `toggle_object_toggle()` to flip the state.
        
    - If toggled **on**: calls `command()` if defined.
        
    - If toggled **off**:
        
        - Calls `command_off()` if defined.
            
        - Otherwise calls `command()` as fallback.
            

### ◼️ Position Behavior Utilities

These methods manage the on-screen positioning of widget objects, especially when widgets move or are updated.

---

#### `update_positions(_object, x, y, avoid_slider=False)`

Updates the **positions of all visual objects** tied to a widget (text, image, background, etc.).

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|Widget to reposition|
|`x`|`int`|New X position|
|`y`|`int`|New Y position|
|`avoid_slider`|`bool`, optional|If `True`, skips updating the slider background (if present). Defaults to `False`.|

Behavior:

- Converts relative to absolute positions.
    
- Uses `_update_position()` to apply updated positions to each object layer.
    

---

#### `_update_position(_object, item, x, y, old_x, old_y)`

Internal helper function to place a **specific item** (image, text, etc.) at a position.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|Widget containing the object|
|`item`|`str`|Name of the attribute (e.g., `image_object`)|
|`x`|`int`|New X position|
|`y`|`int`|New Y position|
|`old_x`|`int`|Previous X position|
|`old_y`|`int`|Previous Y position|

Behavior:

- Adjusts text placement based on justification (left, right, center).
    
- Slightly offsets image positioning to compensate for border width.
    
- Delegates positioning to the master widget’s `object_place()` method.
    

### ◼️ Placement Behavior Utilities

These functions are responsible for the **initial creation and layout** of widget visual elements — such as backgrounds, images, and text — when a widget is first drawn.

---

#### `place_bulk(_object, x, y)`

Places **all visual elements** of a widget at a specified position. Used for bulk layout when initializing a widget.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|The widget whose elements will be placed|
|`x`|`int`|X position (relative)|
|`y`|`int`|Y position (relative)|

Behavior:

- Converts to absolute position using `rel_position_to_abs()`
    
- Creates:
    
    - `bg_object` and `bg_object_active` (if background fills are provided)
        
    - All valid image objects (`image`, `hover_image`, etc.)
        
    - Text and active text (if present)
        
- Populates `_object._images_initialized` with rendered images.
    

---

#### `generate_text(_object, x, y)`

Creates the **text elements** for a widget — including both normal and active text layers.

|Argument|Type|Description|
|---|---|---|
|`_object`|`nebulatk.Widget`|Widget to draw text for|
|`x`|`int`|Absolute X position|
|`y`|`int`|Absolute Y position|

Behavior:

- Calculates horizontal anchor (`center`, `left`, `right`) based on widget justification.
    
- Vertically centers text inside the widget.
    
- Creates:
    
    - `text_object` using `text_color`
        
    - `active_text_object` using `active_text_color` (if specified)
        
- Stores the rendered text into `_object.text_object` and `_object.active_text_object`.
    

