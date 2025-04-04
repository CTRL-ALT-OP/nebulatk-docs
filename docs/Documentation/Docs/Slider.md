# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

A horizontal slider widget that allows dragging a button (thumb) along a track.  
Supports fully customizable thumb styling (colors, images, text), but does not handle value calculations — you can provide a `dragging_command` to track the movement.

---

## `__init__(...)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`root`|`Window` or `_widget`|✅|Parent window or widget.|
|`width`|`int`|✅|Width of the slider track. Defaults to `0`.|
|`height`|`int`|✅|Height of the slider track. Defaults to `0`.|
|`image`|`Image` or `str`|✅|Background image for the slider track.|
|`fill`|`Color` or `str`|✅|Fill color of the track. Defaults to `"default"`.|
|`border`|`Color` or `str`|✅|Border color. Defaults to `"default"`.|
|`border_width`|`int`|✅|Border width of the track. Defaults to `1`.|
|`bounds_type`|`str`|✅|`"box"` or `"non-standard"`. Defaults to `"box"`.|

> **Slider button-specific options**  
> These configure the draggable button (thumb) that slides along the track:

|Argument|Type|Optional|Description|
|---|---|---|---|
|`slider_width`|`int`|✅|Width of the slider thumb button.|
|`slider_height`|`int`|✅|Height of the slider thumb button.|
|`slider_text`|`str`|✅|Optional text inside the slider button.|
|`slider_font`|`Font` or `tuple`|✅|Font used in the slider button.|
|`slider_justify`|`str`|✅|Text justification.|
|`slider_text_color`|`Color` or `str`|✅|Text color in normal state.|
|`slider_active_text_color`|`Color` or `str`|✅|Text color in active state.|
|`slider_fill`|`Color` or `str`|✅|Fill color for the slider button.|
|`slider_active_fill`|`Color` or `str`|✅|Fill color when active.|
|`slider_hover_fill`|`Color` or `str`|✅|Fill color when hovered.|
|`slider_active_hover_fill`|`Color` or `str`|✅|Fill color when active & hovered.|
|`slider_border`|`Color` or `str`|✅|Border color of the slider button.|
|`slider_border_width`|`int`|✅|Thickness of slider button border.|
|`slider_image`|`Image` or `str`|✅|Background image for slider button.|
|`slider_active_image`|`Image` or `str`|✅|Image when active.|
|`slider_hover_image`|`Image` or `str`|✅|Image when hovered.|
|`slider_active_hover_image`|`Image` or `str`|✅|Image when active & hovered.|
|`slider_bounds_type`|`str`|✅|`"box"`, `"non-standard"`, or `"custom"` bounds for thumb.|
|`slider_custom_bounds`|`list`|✅|Custom bounds for slider thumb.|

---

## Methods

### `_dragging(x: int, y: int)`

Handles the dragging logic of the slider.

- Moves the thumb along the X-axis only.
    
- Clamps position within the slider's bounds.
    

✅ **Internal override** used for `dragging_command` of the child button.

---

### `place(x=0, y=0) → self`

### `configure(**kwargs) → self`

### `update()`

### `destroy()`

### `show()` / `hide()` / `visible`

Standard lifecycle methods inherited from `_widget`.

---

## Properties

Inherited from `_widget`, including:

- `x`, `y`, `width`, `height`
    
- `fill`, `image`, `border`, `border_width`
    
- `visible`
    

You can also access the thumb via `self.button`.

---

## Example use case:

```python
from nebulatk import Window, Slider

def on_slide(x, y):
    print(f"Slider moved to x={x}")

win = Window(width=400, height=200)
Slider(
    win,
    width=200,
    height=20,
    fill="#eee",
    border="#aaa",
    border_width=1,
    slider_width=30,
    slider_height=20,
    slider_fill="#ffaaaa",
    slider_border="#d66",
    slider_border_width=2,
    slider_text="|",
).place(100, 80).button.dragging_command = on_slide
```