# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

# Image

A wrapper around `PIL.Image` that supports resizing, flipping, rotating, recoloring, and transparency manipulation.  
Includes built-in support for caching Tkinter-compatible `PhotoImage` instances (via `.tk_image()`), used by `nebulatk` widgets.

---

## `__init__(image, _object=None)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`image`|`str`, `Image`, or `PIL.Image`|❌|Path to an image, existing `Image` instance, or raw `PIL.Image`.|
|`_object`|`Widget`|✅|If provided, the image is resized to fit the widget and converted for Tkinter rendering.|

---

## Methods

---

### `resize(width, height) → self`

Resize the image using nearest-neighbor interpolation.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`width`|int|❌|New width in pixels.|
|`height`|int|❌|New height in pixels.|

---

### `flip(direction="horizontal") → self`

Flip the image horizontally or vertically.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`direction`|str|✅|`"horizontal"` or `"vertical"`.|

---

### `rotate(angle) → self`

Rotate the image by the given angle (in degrees).

|Argument|Type|Optional|Description|
|---|---|---|---|
|`angle`|float|❌|Degrees to rotate.|

---

### `recolor(color) → self`

Tints the image using the given color, preserving alpha.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`color`|`Color` or `str`|❌|Color to apply to the image.|

---

### `set_transparency(transparency) → self`

Set the alpha channel of the entire image to a constant.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`transparency`|int|❌|Value between `0` and `255`.|

---

### `increment_transparency(transparency) → self`

Reduce the alpha channel by a constant value.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`transparency`|int|❌|Amount to subtract from alpha (clamped).|

---

### `set_relative_transparency(transparency, curve="lin", exponent=1) → self`

Applies a curve-based transparency transformation.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`transparency`|int|❌|Target maximum alpha.|
|`curve`|str|✅|`"lin"`, `"exp"`, `"sqrt"`, `"quad"`, `"cubic"`, `"log"`.|
|`exponent`|float|✅|Exponent for exponential curve. Only used if `curve="exp"`.|

---

### `tk_image(_object) → PhotoImage`

Returns the `Tkinter.PhotoImage` corresponding to this image for a given widget’s master. Caches result for reuse.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`_object`|Widget|❌|Used to resolve the correct Tkinter master.|

---

## Example use case:

```python
from nebulatk import Window, Button
from nebulatk.image_manager import Image

img = Image("button.png").resize(120, 60).flip("horizontal")

win = Window(width=400, height=300)
Button(win, image=img).place(140, 100)
```

---

# Utility Functions

---

## `convert_image(_object, image) → PhotoImage`

Converts a `PIL.Image` to a `Tk.PhotoImage` using the provided widget’s master.

---

## `load_image(_object, image, return_both=False)`

Load and optionally resize an image for a widget.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`_object`|Widget|❌|Widget used to determine target size and root context.|
|`image`|`str`|❌|Path to the image.|
|`return_both`|`bool`|✅|Whether to return both the `PhotoImage` and `PIL.Image`.|

**Returns:**

- `TkImage` or `(TkImage, PIL.Image)`
    

---

## `load_image_generic(window, image, return_both=False)`

Like `load_image()`, but doesn’t resize and doesn’t require a widget — just a `Window`.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`window`|`Window`|❌|Window whose Tk root will be used as image master.|
|`image`|`str`|❌|Path to the image file.|
|`return_both`|`bool`|✅|If True, returns both `TkImage` and `PIL.Image`.|

---

## `create_image(fill, width, height, border, border_width, master) → TkImage`

Creates a new in-memory image (solid rectangle with fill and border) and returns a `Tk.PhotoImage`.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`fill`|color|❌|Fill color (RGBA or hex).|
|`width`|int|❌|Width of image in pixels.|
|`height`|int|❌|Height of image in pixels.|
|`border`|color|❌|Border color.|
|`border_width`|int|❌|Thickness of the border.|
|`master`|Window|❌|The `Window` object used to link the `PhotoImage`.|
