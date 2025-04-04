# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

Represents a color object with both hex and RGBA representations. This class extends `str`, allowing it to behave like a string while providing additional functionality for color manipulation.

### **Constructor**

```python
Color(value)
```

|Argument|Type|Description|Optional|
|---|---|---|---|
|`value`|Any|A string (name or hex), RGB/RGBA tuple, or another `Color` object.|No|

### Attributes

- `color` (str): Hex representation of the color.
    
- `rgba` (tuple): RGBA tuple of the color.
    

### Methods

#### `brighten(increment=10)`

Brightens the color by increasing the RGB values.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`increment`|int|Amount to increase RGB values (0–255)|Yes (default: 10)|

**Returns:**  
`Color`: A new brightened color instance.

#### `darken(increment=10)`

Darkens the color by decreasing the RGB values.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`increment`|int|Amount to decrease RGB values (0–255)|Yes (default: 10)|

**Returns:**  
`Color`: A new darkened color instance.

#### `__str__()`

Returns the color as a string (hex value).

**Returns:**  
`str`

#### `__eq__(other)`

Compares this color with another.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`other`|`Color`/str|The color to compare|No|

**Returns:**  
`bool`: Whether the colors are equivalent.

#### `startswith(prefix)`

Checks if the color's hex value starts with a given prefix.

|Argument|Type|Description|Optional|
|---|---|---|---|
|`prefix`|str|Prefix to check for|No|

**Returns:**  
`bool`