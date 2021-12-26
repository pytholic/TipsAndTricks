# Notes

## Changing Background colors
### TextFormField
* Use `fillColor` and `filled` attributes of InputDecoration
```dart
TextFormField(
  decoration: InputDecoration(
    filled: true,
    labelText: "Name",
    fillColor: Colors.black,
    ),
   ),
```

### Row(), Column() and some other objects
* Wrap them inside a `Container()
```dart
Container (
  color: Colors.white,
  child: Row(
    .
    .
    .
    ),
   ),
```
