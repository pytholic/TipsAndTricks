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

## Changing app display name
To change the app display name under the app `icon`. \
For Android:
* Open `AndroidManifest.xml` (located at `android/app/src/main`)
* Insert you app name in the following field.
```html
<application
    android:label="App Name" ...> // Your app name here
```

For iOS:
* Open `info.plist` (located at `ios/Runner`)
* Insert you app name in the following field.
```html
<key>CFBundleName</key>
<string>App Name</string> // Your app name here
```

## Changing app icon


### Issue
```
Unhandled exception:
FormatException: Invalid number (at character 1)
```

In `lib/android.dart`, change:
```dart
    if (line.contains('minSdkVersion')) {
      // remove anything from the line that is not a digit
      final String minSdk = line.replaceAll(RegExp(r'[^\d]'), '');
      return int.parse(minSdk);
    }
  }
  return 0; // Didn't find minSdk, assume the worst
```

to

```dart
    if (line.contains('minSdkVersion')) {
      // remove anything from the line that is not a digit
      final String minSdk = line.replaceAll(RegExp(r'[^\d]'), '');
      try {
        return int.parse(minSdk);
      } on FormatException catch (_) {
        printStatus("minSdk '${minSdk}' cannot be parsed as int ");
      }
    }
  }
  return 0; // Didn't find minSdk, assume the worst
```
