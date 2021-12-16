# Notes

## Widget design
Defining widget dimentions in python `add_widget` code is rudimentary way of doing things.

Kivy has a whole design language. With that design language, we abstarct away all this widget design settings away into a separate file. Sort of like **CSS/html** file, where all the design stuff is defined in the CSS fiel and we just reference it in our module.

We use latter method most of the time instead of explicitly putting things in out python code.

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
                                      