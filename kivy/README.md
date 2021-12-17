# Notes

## Widget design
Defining widget dimentions in python `add_widget` code is rudimentary way of doing things.

Kivy has a whole design language. With that design language, we abstarct away all this widget design settings away into a separate file. Sort of like **CSS/html** file, where all the design stuff is defined in the CSS fiel and we just reference it in our module. Always good to keep main code and design files separate from each other.

We use latter method most of the time instead of explicitly putting things in out python code.

* Design file should have same name without App part i.e. If main class is `MyApp` then design file should be names `My.kv`. Using `myapp.kv` will throw an error.
* We can use `Builder` to get around above notation and using any name for the file.
* When we run, kivy looks for this file by default, and we do not need to reference it or write anything in the main file.
* Adding `size: root.width, root.height` is important and fixes the design to the window size.
* Method `press` requires `(self, isntance)` in python design but only `self` in `.kv` design.

## Setting widget height and width
* We can pass `height` and `width` while defining widgets. 
* Important to set `size_hint_x=None` or `size_hint_y=None`. We can also do this as `size_hint = (None, None)`.
* we can also use `size_hint` for resizing widgets.
* If multiple widgets have same dimentions, we can force same dimensions for all of them while defining `GridLayout()`.

```python
# Create buttons grid layout
self.button_grid = GridLayout(row_force_default=True,
                              row_default_height=50,
                              col_force_default=True,
                              col_default_height=100)

```

* Using `BoxLayout` for buttons is good.

## Changing background color
### Method # 1
CHanging in `.kv` file.

```
canvas.before:
  Color:
  	rgba: (1,1,1,0.4)
  Rectangle:
  	pos: self.pos
  	size: self.size
```

### Method # 2
Change in main app file.
```
from kivy.core.window import Window

class MyApp(App):
    def build(self):
        Window.clearcolor = (1,1,1,1)
        return MyLayout()
```