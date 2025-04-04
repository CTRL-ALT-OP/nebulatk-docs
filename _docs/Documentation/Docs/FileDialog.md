# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

A wrapper around `tkinter.filedialog.askopenfile()` that integrates with the `nebulatk` event system.  
Allows users to select a file via a native file dialog while ensuring the window correctly handles focus and hover state before and after.

---

## `FileDialog(window, initialdir=None, mode="r", filetypes=(("All files", "*")) )`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`window`|`nebulatk.Window`|❌|The root `nebulatk.Window` instance using the dialog.|
|`initialdir`|`str`|✅|Directory path to open initially. Defaults to `None`.|
|`mode`|`str`|✅|File open mode, like `"r"`, `"rb"`, etc. Defaults to `"r"`.|
|`filetypes`|`list[tuple]`|✅|A list of filetype descriptions, e.g. `[("Text files", "*.txt")]`.|

---

### Returns:

- A file-like object (`_io.TextIOWrapper` or `_io.BufferedReader`) opened in the specified mode,  
    or `None` if the dialog is cancelled.
    

---

## Example use case:

```python
from nebulatk import Window, FileDialog, Button

def open_file():
    file = FileDialog(win)
    if file:
        print("Selected:", file.name)

win = Window(width=400, height=200)
Button(win, text="Open File", command=open_file).place(100, 80)
```