# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

## Module: `defaults`

### Overview

The `defaults` module provides a convenient base for defining default appearance values (colors, fonts, etc.) for widgets in the `nebulatk` framework. It allows setting and adjusting baseline design elements like fill, border, text color, and font.

---

### Functions

#### `_offset(initial, amount)`

Returns a brighter or darker version of a color depending on whether it is closer to black or white.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`initial`|`Color`|The original color to modify.|No|
|`amount`|`int`|The amount by which to adjust brightness (0–255).|No|

**Returns:** `Color` – The adjusted color.

---

### Classes

#### `new`

A container for default configuration values. Currently, only a default constructor is supported; attempting to load from a file raises a warning.

##### Constructor

```python
new(file=None)
```

|Argument|Type|Description|Optional|
|---|---|---|---|
|`file`|`str`|Not yet implemented; raises warning if used|Yes|

##### Attributes

|Attribute|Type|Description|
|---|---|---|
|`default_text_color`|`Color`|Default color for widget text (black)|
|`default_fill`|`Color`|Default fill color (white)|
|`default_border`|`Color`|Default border color (black)|
|`default_font`|`Font`|Default font object (`"Helvetica", -1`)|
