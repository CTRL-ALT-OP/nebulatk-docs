# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

A non-interactive text display widget.  
Labels support custom fonts, alignment, fill colors, borders, and optional background images. Inherits from `_widget`.

---

## `__init__(...)`

| Argument       | Type                  | Optional | Description                                                        |
| -------------- | --------------------- | -------- | ------------------------------------------------------------------ |
| `root`         | `Window` or `_widget` | ✅        | Parent window or widget.                                           |
| `width`        | `int`                 | ✅        | Width in pixels. Defaults to `0`.                                  |
| `height`       | `int`                 | ✅        | Height in pixels. Defaults to `0`.                                 |
| `orientation`  | `int`                 | ✅        | Rotation angle in degrees. Defaults to `0`.                        |
| `text`         | `str`                 | ✅        | Text to display. Defaults to `""`.                                 |
| `font`         | `Font` or `tuple`     | ✅        | Font name or tuple. Defaults to system default.                    |
| `justify`      | `str`                 | ✅        | `"left"`, `"center"`, or `"right"`. Defaults to `"center"`.        |
| `text_color`   | `Color` or `str`      | ✅        | Text color. Defaults to `"default"`.                               |
| `fill`         | `Color` or `str`      | ✅        | Background fill color. Defaults to `"default"`.                    |
| `border`       | `Color` or `str`      | ✅        | Border color. Defaults to `"default"`.                             |
| `border_width` | `int`                 | ✅        | Thickness of the border in pixels. Defaults to `0`.                |
| `image`        | `Image` or `str`      | ✅        | Background image. Defaults to `None`.                              |
| `bounds_type`  | `str`                 | ✅        | `"box"`, `"non-standard"`, or `"custom"`. Defaults to `"default"`. |

---

## Methods

Label inherits all relevant methods from `_widget`, but does **not override** any of them. It disables interactivity by default.

### `place(x=0, y=0) → self`

Position the label at `(x, y)` on the canvas.

---

### `configure(**kwargs) → self`

Dynamically update text, font, colors, etc.

---

### `update()`

Redraw the label’s visuals.

---

### `destroy()`

Remove the label from its parent and delete its visuals.

---

### `show()` / `hide()` / `visible`

Show or hide the label.

---

## Properties (inherited from `_widget`)

- `text`, `font`, `justify`, `text_color`
    
- `fill`, `border`, `border_width`
    
- `image`, `bounds_type`
    
- `x`, `y`, `width`, `height`
    
- `visible`, `orientation`
    

---

## Example use case:

```python
from nebulatk import Window, Label

win = Window(width=400, height=200)
Label(
    win,
    text="Status: OK",
    font=("Helvetica", 18),
    text_color="#222",
    fill="#e0ffe0",
    border="#88cc88",
    border_width=2,
).place(100, 80)
```