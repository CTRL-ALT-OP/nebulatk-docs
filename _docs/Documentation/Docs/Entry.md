# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

An editable, single-line text input widget.  
Supports typing, font configuration, and visual styling. Inherits from `_widget`, and is the only widget with `can_type = True`.

---

## `__init__(...)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`root`|`Window` or `_widget`|✅|Parent window or container.|
|`width`|`int`|✅|Width in pixels. Defaults to `0`.|
|`height`|`int`|✅|Height in pixels. Defaults to `0`.|
|`orientation`|`int`|✅|Rotation angle in degrees. Defaults to `0`.|
|`text`|`str`|✅|Initial text content. Defaults to `""`.|
|`font`|`Font` or `tuple`|✅|Font name or tuple (e.g., `("Arial", 14)`).|
|`justify`|`str`|✅|Text alignment (`"left"`, `"center"`, `"right"`). Defaults to `"center"`.|
|`text_color`|`Color` or `str`|✅|Text color. Defaults to `"default"`.|
|`fill`|`Color` or `str`|✅|Background fill color. Defaults to `"default"`.|
|`border`|`Color` or `str`|✅|Border color. Defaults to `"default"`.|
|`border_width`|`int`|✅|Thickness of border. Defaults to `0`.|
|`image`|`Image` or `str`|✅|Background image. Defaults to `None`.|
|`bounds_type`|`str`|✅|`"box"`, `"non-standard"`, or `"custom"`. Defaults to `"default"`.|

---

## Methods

### `typed(character: str)`

Handles character input.

- Supports typing alphanumerics and backspace.
    
- Updates `entire_text` and visible `text` based on available space.
    

✅ **Overrides** `_widget.typed`

---

### `get() → str`

Returns the current full text (including clipped parts not currently visible).

✅ **New Method**

---

### `place(x=0, y=0) → self`

### `configure(**kwargs) → self`

### `update()`

### `destroy()`

### `show()` / `hide()` / `visible`

Standard widget lifecycle and visual management.  
✅ **Inherited from `_widget` and `Component`**

---

## Properties (inherited from `_widget`)

- `text`, `font`, `text_color`, `justify`
    
- `fill`, `border`, `border_width`
    
- `image`, `bounds_type`
    
- `x`, `y`, `width`, `height`
    
- `visible`
    

---

## Example use case:

```python
from nebulatk import Window, Entry

win = Window(width=400, height=200)
entry = Entry(
    win,
    text="Start typing...",
    font=("Arial", 18),
    fill="#fefefe",
    border="#cccccc",
    border_width=2,
).place(100, 80)

# Later you can retrieve the text:
# typed_text = entry.get()
```