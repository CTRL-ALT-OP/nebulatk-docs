# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

A foundational class for building custom GUI components in the `nebulatk` framework.  
Provides support for layout (size/position), appearance (colors, fonts, images), interactivity (hover/click), and visual updating.

This class is not meant to be used directly. Subclass it to build components like `Button`, `Label`, `Slider`, or your own custom widgets.

---

## `__init__(...)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`root`|`Window` or `_widget`|✅|Parent widget or window.|
|`width`|`int`|✅|Width in pixels. Defaults to `0`.|
|`height`|`int`|✅|Height in pixels. Defaults to `0`.|
|`orientation`|`int`|✅|Rotation angle in degrees. Defaults to `0`.|
|`text`|`str`|✅|Text content. Defaults to `""`.|
|`font`|`Font` or `tuple`|✅|Font name or tuple. Defaults to `"default"`.|
|`justify`|`str`|✅|Text alignment (`"left"`, `"center"`, `"right"`). Defaults to `"center"`.|
|`text_color`|`Color` or `str`|✅|Text color. Defaults to `"default"`.|
|`active_text_color`|`Color` or `str`|✅|Active text color. Defaults to `None`.|
|`fill`|`Color` or `str`|✅|Background fill color. Defaults to `"default"`.|
|`active_fill`|`Color` or `str`|✅|Fill when active. Defaults to `"default"`.|
|`hover_fill`|`Color` or `str`|✅|Fill when hovered. Defaults to `"default"`.|
|`active_hover_fill`|`Color` or `str`|✅|Fill when active and hovered. Defaults to `"default"`.|
|`border`|`Color` or `str`|✅|Border color. Defaults to `"default"`.|
|`border_width`|`int`|✅|Border thickness. Defaults to `0`.|
|`image`|`Image` or `str`|✅|Background image. Defaults to `None`.|
|`active_image`|`Image` or `str`|✅|Image when active. Defaults to `None`.|
|`hover_image`|`Image` or `str`|✅|Image when hovered. Defaults to `None`.|
|`active_hover_image`|`Image` or `str`|✅|Image when active and hovered. Defaults to `None`.|
|`bounds_type`|`str`|✅|`"box"`, `"non-standard"`, `"custom"`. Defaults to `"default"`.|
|`custom_bounds`|`list`|✅|Custom polygon hitboxes. Used if `bounds_type="custom"`.|
|`command`|`Callable`|✅|Function to call on click. Defaults to `None`.|
|`command_off`|`Callable`|✅|Function to call when toggled off. Defaults to `None`.|
|`dragging_command`|`Callable`|✅|Function called on drag. Defaults to `None`.|
|`mode`|`str`|✅|`"standard"` or `"toggle"`. Defaults to `"standard"`.|
|`state`|`bool`|✅|Initial toggle state. Defaults to `False`.|

---

## Methods

---

### `hovered()`

Trigger hover behavior if `can_hover` is enabled.

---

### `hover_end()`

Remove hover state and update visuals.

---

### `clicked()`

Trigger click behavior depending on `mode`.

- In `"toggle"` mode: flip state and call `command` or `command_off`.
    
- In `"standard"` mode: call `command`.
    

---

### `release()`

Called when mouse is released. Toggles off in `"standard"` mode and calls `command_off` if applicable.

---

### `toggle()`

Toggles the widget state and appearance if `mode="toggle"`.

---

### `dragging(x, y)`

Triggers the assigned `dragging_command` (if set) using relative position.

---

### `typed(character: str)`

Called when the widget receives a keystroke.  
Only functional when `can_type = True` (e.g., `Entry`).  
Handles backspace, appending text, and dynamic slicing.

---

### `change_active()`

Placeholder method — can be overridden for toggling visual state.  
Used internally, currently does nothing by default.

---

### `place(x=0, y=0) → self`

Places the widget at canvas coordinates `(x, y)` and updates children.

---

### `update()`

Redraw and reapply widget visuals: size, position, text, bounds, etc.

---

### `destroy()`

Remove the widget from the root and delete visuals.

---

### `show()` / `hide()` / `visible`

Shows or hides the widget. `visible` can also be set as a boolean property.

---

### `configure(**kwargs) → self`

Update any widget configuration (font, text, fill, etc.) dynamically.

---

## Properties (with both getters/setters)

- `x`, `y`, `width`, `height`: Geometry
    
- `text`, `font`, `justify`: Text
    
- `fill`, `hover_fill`, `active_fill`, `active_hover_fill`: Colors
    
- `text_color`, `active_text_color`: Text colors
    
- `border`, `border_width`: Borders
    
- `image`, `hover_image`, `active_image`, `active_hover_image`: Images
    
- `orientation`: Rotation angle
    
- `bounds_type`, `bounds`: Hitbox behavior
    

---

## Example use case: Custom Widget

```python
from nebulatk import _widget, Window

class TagLabel(_widget):
    def __init__(self, root, text):
        super().__init__(
            root=root,
            text=text,
            font=("Arial", 14),
            fill="#ddddff",
            text_color="#222",
            border="#8888ff",
            border_width=1,
        )
        self.can_hover = False
        self.can_click = False
        self.can_type = False

win = Window(width=300, height=200)
TagLabel(win, "Hello world").place(20, 40)
```