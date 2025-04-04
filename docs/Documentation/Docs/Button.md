# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

An interactive, clickable widget that supports text, images, borders, hover effects, and toggle modes. Can execute commands on click or toggle state. Inherits all properties and behavior from `_widget`.

---

## `__init__(...)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`root`|`Window` or `_widget`|✅|The parent container or root window.|
|`width`|`int`|✅|Width of the button in pixels. Defaults to `0`.|
|`height`|`int`|✅|Height of the button in pixels. Defaults to `0`.|
|`text`|`str`|✅|Text label displayed on the button. Defaults to `""`.|
|`font`|`Font` or `tuple`|✅|Font name or tuple (e.g., `("Arial", 16)`).|
|`justify`|`str`|✅|Text alignment: `"left"`, `"center"`, `"right"`. Defaults to `"center"`.|
|`text_color`|`Color` or `str`|✅|Text color in default state. Defaults to `"default"`.|
|`active_text_color`|`Color` or `str`|✅|Text color in active state. Defaults to `None`.|
|`fill`|`Color` or `str`|✅|Background fill color. Defaults to `"default"`.|
|`active_fill`|`Color` or `str`|✅|Background fill when active. Defaults to `"default"`.|
|`hover_fill`|`Color` or `str`|✅|Background fill on hover. Defaults to `"default"`.|
|`active_hover_fill`|`Color` or `str`|✅|Fill when both active and hovered. Defaults to `"default"`.|
|`border`|`Color` or `str`|✅|Border color. Defaults to `"default"`.|
|`border_width`|`int`|✅|Thickness of border in pixels. Defaults to `0`.|
|`image`|`Image` or `str`|✅|Default background image. Defaults to `None`.|
|`active_image`|`Image` or `str`|✅|Background image when active. Defaults to `None`.|
|`hover_image`|`Image` or `str`|✅|Image on hover. Defaults to `None`.|
|`active_hover_image`|`Image` or `str`|✅|Image when both active and hovered. Defaults to `None`.|
|`bounds_type`|`str`|✅|`"box"`, `"non-standard"`, or `"custom"`. Defaults to `"default"`.|
|`custom_bounds`|`list`|✅|Polygon bounds for non-rectangular shapes. Defaults to `None`.|
|`command`|`Callable`|✅|Function to call when clicked. Defaults to `None`.|
|`command_off`|`Callable`|✅|Function called when toggled off. Only used in `"toggle"` mode.|
|`dragging_command`|`Callable`|✅|Function triggered when dragged. Defaults to `None`.|
|`mode`|`str`|✅|`"standard"` or `"toggle"`. Defaults to `"standard"`.|
|`state`|`bool`|✅|Initial state (`True` for active). Defaults to `False`.|

---

## Methods

### `clicked()`

Triggers when the button is clicked.  
If in `"toggle"` mode, flips `state` and calls `command` or `command_off`.

---

### `release()`

Called when the mouse button is released.  
If the widget was clicked in `"standard"` mode, it toggles `state`, updates appearance, and may call `command_off`.

---

### `hovered()`

Activates the visual hover effect.

---

### `hover_end()`

Removes the hover state.

---

### `toggle()`

Toggles the visual and logical state of the button (used in toggle mode).

---

### `dragging(x: int, y: int)`

Handles mouse drag event. Converts to relative position and calls `dragging_command`.

---

### `destroy()`

Removes the widget from the window and cleans up.

---

### `place(x=0, y=0) → self`

Places the widget on the canvas at position `(x, y)`.

---

### `configure(**kwargs) → self`

Dynamically update any configuration options (text, image, fill, etc.).

---

### `show()` / `hide()` / `visible`

Show or hide the widget. Also accessible via `visible` property.

---

### `update()`

Redraws and refreshes the widget, including text, images, position, and colors.

---

## Example use case:

```python
from nebulatk import Window, Button

def on_click():
    print("Button clicked!")

win = Window(width=400, height=300)
Button(
    win,
    text="Click Me!",
    fill="#040404",
    text_color="#ffffff",
    border="#aaaaaa",
    border_width=2,
    command=on_click,
).place(100, 100)
```