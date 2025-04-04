Generally, the formatting of NebulaTk is very similar to Tkinter. However, there are some key differences.

One large difference is the ability to chain functions together.
Example:
Tkinter:
```python
button = tk.Button(root)
button.place(x=0, y=0)
```
NebulaTk:
```python
button = ntk.Button(root).place(x=0, y=0)
```

Another key difference is the ability to use properties, rather than having to use configure functions. However, using configure is still suggested, as by default the widget will not update after changing a property directly.
Example:
Tkinter:
```python
label = tk.Label(root, text="Hi")
label.place(x=0, y=0)
label.configure(text = "Hello")
```
NebulaTk:
```python
label = ntk.Label(root, text="Hi").place()
label.text = "Hello"
```

NebulaTk also seeks to have as many optional arguments as possible, to prevent constantly having to pass in unnecessary values.
Example:
Tkinter:
```python
label = tk.Label(root, text="Hi")
label.place(x=0, y=0)
```
NebulaTk:
```python
label = ntk.Label(root, text="Hi").place()
```

NebulaTk also aims to have as much consistency in function names as possible, and merging functions into the constructor when possible.
Example:
Tkinter:
```python
root = tk.Tk()
root.geometry("750x250+400+300")
root.title("New Window")
```
NebulaTk:
```python
root = ntk.Window(width=750, height=250).place(x=400, x=300)
```