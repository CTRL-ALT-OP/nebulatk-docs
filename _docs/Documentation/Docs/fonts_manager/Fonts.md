# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

Thanks! Here’s the full documentation for the `fonts_manager` module, which handles font loading, sizing, and text fitting for the `nebulatk` UI system.

---

# `fonts_manager`

Provides utilities for working with fonts in `nebulatk`, including:

- Font sizing to fit a widget
    
- Minimum button dimensions for a given font/text
    
- Slicing text to fit within width
    
- Loading custom fonts (Windows-only)
    
- Character sets for filtering input
    

---

# Class: `Font`

Wraps font creation for consistency with other `nebulatk` styling tools.

---

## `__init__(font)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`font`|`str`, `tuple`, or `None`|❌|Font name, font tuple `(name, size)`, or `"default"` for system fallback.|

### Behavior:

- `"default"` or `None` → `("Helvetica", -1)` (will auto-adjust later)
    
- `"Arial"` → `("Arial", 10)`
    
- `("Arial", 14)` → used directly
    

---

## Properties:

- `font`: Tuple format of `(name, size)` used by Tkinter
    

---

## Example:

```python
from nebulatk.fonts_manager import Font

f1 = Font("Arial").font          # ("Arial", 10)
f2 = Font(("Verdana", 12)).font  # ("Verdana", 12)
f3 = Font(None).font             # ("Helvetica", -1)
```

---

# Function: `loadfont(fontpath, private=True, enumerable=False)`

Loads a custom `.ttf` or `.otf` font on Windows using the `ctypes` WinAPI.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`fontpath`|str|❌|Path to the `.ttf` or `.otf` file.|
|`private`|bool|✅|If True, font is only visible to this process. Defaults to `True`.|
|`enumerable`|bool|✅|If False, font won’t show up in font lists. Defaults to `False`.|

### Returns:

- `True` if font was successfully loaded, `False` otherwise.
    

---

# Function: `get_max_font_size(root, font, width, height, text)`

Returns the **maximum font size** that allows `text` to fit within a given width and height.

|Argument|Type|Description|
|---|---|---|
|`root`|`Window`|The base `nebulatk.Window` object.|
|`font`|`tuple`|Font in `(name, size)` format. Size is ignored.|
|`width`|`int`|Width constraint.|
|`height`|`int`|Height constraint.|
|`text`|`str`|Text to measure.|

### Returns:

- `int`: Maximum size (in points) that fits both dimensions.
    

---

# Function: `get_min_button_size(root, font, text)`

Returns the **minimum (width, height)** that a button must have to display the given text and font.

|Argument|Type|Description|
|---|---|---|
|`root`|`Window`|The root `Window`.|
|`font`|`tuple`|Font name and size.|
|`text`|`str`|Text to fit.|

### Returns:

- `(width, height)` as integers
    

---

# Function: `get_max_length(root, text, font, width, end=0)`

Returns the maximum **number of characters** that can fit in the given width.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`root`|`Window`|❌|Root window|
|`text`|`str`|❌|Text to slice|
|`font`|`tuple`|❌|Font used for measuring|
|`width`|`int`|❌|Width constraint|
|`end`|`int`|✅|Index to slice up to (default is end of string)|

### Returns:

- `int`: Max length of string slice that fits
    

---

# Character Sets

These are used for input validation or filtering in typing widgets:

|Name|Type|Description|
|---|---|---|
|`ALPHA`|`list`|All lowercase + uppercase letters|
|`NUMERIC`|`list`|Digits 0-9|
|`SYMBOL`|`list`|Common punctuation/symbols|
|`ALPHANUMERIC`|`list`|Combined letters and digits|
|`ALPHANUMERIC_PLUS`|`list`|Alphanumerics + symbols|

---

## Example usage in Entry widget:

```python
from nebulatk.fonts_manager import ALPHANUMERIC

if char in ALPHANUMERIC:
    entry.entire_text += char
```

---

Let me know if you'd like to continue with `colors_manager`, or move on to `standard_methods` or one of the others!