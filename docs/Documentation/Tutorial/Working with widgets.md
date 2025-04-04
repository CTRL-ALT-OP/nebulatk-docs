Now that you have a window created, we can start adding widgets.

Let's start by adding a Label to the window. Just like the window, we can immediately place it. If we don't specify where to put it, it will placed at 0,0.
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)
label = ntk.Label(root, text="Hello World!").place()
```

Because we can create and place the label in one line, if we don't want to do anything with this label in the future, we don't have to assign it to a variable. This enables us to clean up the variables used in our program, and only assign variable names when we actually need to.
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)
ntk.Label(root, text="Hello World!").place()
```

We also can always access the widgets in the window by looking at the `.children` variable. This variable also exists for all widgets, for example if you placed a button inside of a frame.

For example, in our previous code, if we later wanted to destroy all the widgets in the window, we would still be able to do that without storing the widgets in variables.
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)
ntk.Label(root, text="Hello World!").place()

for widget in root.children:
	print(f"Deleting a {child.__name__} widget!")
	child.destroy()
```

If we placed the labels inside a frame, we could do it like this:
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)

frame = ntk.Frame(root).place()

ntk.Label(frame, text="Hello World!").place()

for widget in frame.children:
	print(f"Deleting a {child.__name__} widget!")
	child.destroy()
```

Deleting a parent widget will also delete all of its children.

