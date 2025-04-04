# WARNING: This document has been generated using AI. A human-written version is underway. Please only use this for basic reference, and do not treat it as accurate.
### Estimated accuracy score: 90% (This means about 10% is WRONG!)

# `Window`

Creates a new top-level application window with a canvas for rendering all widgets.  
Runs in a **separate thread** to safely handle Tkinter's mainloop alongside the main Python process.

The returned object is an instance of `_window_internal`.

---

## `Window(...)`

|Argument|Type|Optional|Description|
|---|---|---|---|
|`width`|`int`|✅|Width of the window in pixels. Defaults to `500`.|
|`height`|`int`|✅|Height of the window in pixels. Defaults to `500`.|
|`title`|`str`|✅|Window title. Defaults to `"ntk"`.|
|`canvas_width`|`int` or `"default"`|✅|Internal canvas width. Defaults to match `width`.|
|`canvas_height`|`int` or `"default"`|✅|Internal canvas height. Defaults to match `height`.|
|`closing_command`|`Callable`|✅|Function called when window is closed. Defaults to `None`.|
|`resizable`|`bool` or tuple|✅|Whether the window is resizable. A single bool or tuple of `(x, y)`.|
|`override`|`bool`|✅|Whether to remove the window frame (for custom styling). Defaults to `False`.|

---

### Returns:

- A `Window` object (internally a `_window_internal` instance), which is immediately usable and rendered.
    

---

## Example use case:

```python
from nebulatk import Window, Label

win = Window(width=400, height=300, title="My App")
Label(win, text="Hello!").place(150, 100)
```

---

# `_window_internal`

This is the actual class returned by `Window()`. It extends:

- `threading.Thread` — to safely run the Tkinter mainloop
    
- `Component` — for layout and visibility
    

---

## Key Methods

---

### `place(x=0, y=0) → self`

Places the window on the screen at screen coordinates `(x, y)`.  
Wraps `root.geometry(...)`.

---

### `resize(width=None, height=None) → self`

Resize the window and canvas.

|Argument|Type|Optional|Description|
|---|---|---|---|
|`width`|int|✅|New window width|
|`height`|int|✅|New window height|

---

### `configure(**kwargs) → self`

Update window properties dynamically.

Supported keys:

- `width`, `height`
    
- `title`
    
- `resizable` (bool or tuple)
    

If `_object` is passed, it will call `canvas.itemconfigure(_object, ...)` instead.

---

### `bind(key, command)`

Bind a keyboard key (e.g. `"<Escape>"`) to a handler function.

---

### `show() → self`

### `hide() → self`

Show or hide the window (using `deiconify()` and `withdraw()`).

---

### `update()`

Force an update/redraw of the window and canvas.  
Wraps `root.update()`.

---

### `close()` / `destroy()`

Safely terminates the mainloop and thread. Also calls `closing_command` if defined.

---

## Canvas Methods

These mirror many `tk.Canvas` functions, but integrate with `nebulatk`:

- `create_image(...)`
    
- `create_rectangle(...)`
    
- `create_text(...)`
    
- `move(_object, x, y)`
    
- `object_place(_object, x, y)`
    
- `delete(_object)`
    
- `change_state(_object, state)`
    

---

## Event Hooks

The window automatically handles:

- Mouse clicks and releases
    
- Hover and leave events
    
- Dragging
    
- Typing into active widgets
    

Handled via internal overrides:

- `click()`, `click_up()`, `hover()`, `leave_window()`, `typing()`
    

---

## Properties

|Property|Type|Description|
|---|---|---|
|`root`|`tk.Tk`|The underlying Tkinter window.|
|`canvas`|`tk.Canvas`|The drawing area used for all widgets.|
|`title`|`str`|Title text shown in window bar.|
|`children`|`list`|List of all widgets created under this window.|
|`updates_all`|`bool`|Whether widget setters should auto-update.|
|`running`|`bool`|Set to `False` when the window is closing.|
|`images`|`dict`|Image references held to prevent garbage collection.|

---

## Example: Resizing, hiding, and updating

```python
win = Window(width=500, height=400)

# Change title and make non-resizable
win.configure(title="Resized!", resizable=(False, False))

# Resize window after 2 seconds
from time import sleep
sleep(2)
win.resize(800, 600)

# Hide and show window later
win.hide()
sleep(1)
win.show()
```