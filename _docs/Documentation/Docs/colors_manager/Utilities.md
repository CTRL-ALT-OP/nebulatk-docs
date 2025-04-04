# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

## Module Functions

---

### `convert_to_hex(color)`

Converts an arbitrary color format to a hex string.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`color`|`str`, `tuple`, `list`, or `Color`|A named color, hex string, RGB/RGBA tuple, or `Color` object.|No|

**Returns:**  
`str`: A hex string representing the color.

**Example:**

```python
convert_to_hex("red")        # returns "#FF0000"
convert_to_hex((255, 255, 0)) # returns "#ffff00"
```

---

### `convert_to_rgb(color)`

Converts an arbitrary color to an RGBA tuple. If RGB is given, alpha is assumed to be 255.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`color`|`str`, `tuple`, `list`, or `Color`|A named color, hex string, RGB/RGBA tuple, or `Color` object.|No|

**Returns:**  
`tuple`: An RGBA color tuple.

**Example:**

```python
convert_to_rgb("#ff0000")     # returns (255, 0, 0, 255)
convert_to_rgb("green")       # returns (0, 128, 0, 255)
```

---

### `check_full_white_or_black(color)`

Checks whether a given color is fully white or fully black.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`color`|Any|The color to check.|No|

**Returns:**  
`int`:

- `1` if fully white `(255, 255, 255)`
    
- `-1` if fully black `(0, 0, 0)`
    
- `0` otherwise
    

**Example:**

```python
check_full_white_or_black("#000000")  # returns -1
check_full_white_or_black("#ffffff")  # returns 1
```
### `colors`

A dictionary mapping standard color names to their corresponding hex strings and RGB values. This is used internally by the `convert_to_hex` and `convert_to_rgb` functions to resolve named colors.

|Key|Type|Description|
|---|---|---|
|`str`|`dict`|Color name (e.g., `"red"`, `"gray30"`, `"skyblue4"`)|

Each entry maps a color name to a list:

```python
colors["skyblue4"]  # returns ["#4A708B", [74, 112, 139]]
```

**Structure:**

```python
colors = {
    "colorname": ["#HEXCODE", [R, G, B]],
    ...
}
```

This dictionary includes a comprehensive set of standard web colors and extended color variations.
