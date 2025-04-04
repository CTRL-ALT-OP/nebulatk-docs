# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

A non-interactive container widget used for grouping and visually separating other widgets.  
Supports background colors, borders, images, and basic layout. Does **not** support clicking, hovering, or typing. Inherits from `_widget`.

---

## `__init__(...)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`root`|`Window` or `_widget`|✅|Parent window or widget.|
|`width`|`int`|✅|Width in pixels. Defaults to `0`.|
|`height`|`int`|✅|Height in pixels. Defaults to `0`.|
|`image`|`Image` or `str`|✅|Optional background image. Defaults to `None`.|
|`fill`|`Color` or `str`|✅|Background fill color. Defaults to `"default"`.|
|`border`|`Color` or `str`|✅|Border color. Defaults to `"default"`.|
|`border_width`|`int`|✅|Border thickness in pixels. Defaults to `1`.|
|`bounds_type`|`str`|✅|`"box"` or `"non-standard"`. Defaults to `"box"`.|

---

## Methods

### `place(x=0, y=0) → self`

Position the frame on the canvas.

---

### `configure(**kwargs) → self`

Update properties like `fill`, `border`, or `image` dynamically.

---

### `update()`

Redraw and refresh the visual frame.

---

### `destroy()`

Remove the frame and all of its visuals.

---

### `show()` / `hide()` / `visible`

Show or hide the frame.

---

## Properties

Inherited from `_widget`:

- `x`, `y`, `width`, `height`
    
- `fill`, `image`, `border`, `border_width`
    
- `bounds_type`
    
- `visible`
    

---

## Example use case:

```python
from nebulatk import Window, Frame, Label

win = Window(width=400, height=300)

# A background frame with a label placed inside it
Frame(
    win,
    width=300,
    height=200,
    fill="#f0f0f0",
    border="#cccccc",
    border_width=2,
).place(50, 50)

Label(
    win,
    text="Settings",
    font=("Arial", 16),
    fill="#f0f0f0",
).place(60, 60)
```