Once you have NebulaTk installed, you can create your first window.

First, import NebulaTk.
```python
import nebulatk as ntk
```

Next, we can create a window. ntk.Window() is the window constructor.
```python
import nebulatk as ntk

root = ntk.Window()
```

We can technically stop here! NebulaTk does not have a mainloop that needs to be run, so this code will create a basic window. You can run the code now to see it.

However, you likely want to do more with the window.

First, lets rename the window. We can do this by passing in the title argument.
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!")
```

We also might want to move the window so that it is placed at a default position, rather than randomly. There is one main way you can do this. It uses the `.place` function, which is identical to widgets.

Option 1:
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!")
root.place(x=200,y=500)
```

NebulaTk allows you to chain together functions as much as we want, so we can place the window on the same line we create it.
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)
```


Because NebulaTk also has no mainloop, we can create more windows using the same process.

```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)
root2 = ntk.Window(title="My second window!").place(x=300,y=600)
```

We now have two windows. There is no "parent" window, so we can close the first window without affecting the second window. They are entirely separated, and should be treated as such.

Because there is no mainloop, you may also have noticed that your code finishes executing, but the windows stay visible. You can confirm this by adding a `quit()` to the bottom of your code:
```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)
root2 = ntk.Window(title="My second window!").place(x=300,y=600)
quit()
```

This is very useful, but could be problematic, as your program might finish, but won't close the windows if you don't tell it to.
If you need to close the windows at any point from the program, you can call `destroy()` or `close()` on them. Again, notice how windows are treated very similar to widgets, as `destroy()` is also how you delete a widget.

```python
import nebulatk as ntk

root = ntk.Window(title="My first window!").place(x=200,y=500)
root2 = ntk.Window(title="My second window!").place(x=300,y=600)

root.destroy()
root2.destroy()
```
