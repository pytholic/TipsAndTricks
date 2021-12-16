# Python-Tips
Useful python shorcuts, tips and functions.

## Reversing a list/array
```python
arr = np.array([1, 2, 3]

# Method 1
arr_reversed = arr[::-1]  # a[start:stop:step]

# Method 2
arr_reversed = np.array(sorted(list(arr), reverse=True))
```

## Running one python script inside another
Use `runpy` module.

```python 
import runpy
runpy.run_path(path_name='hello.py')
```