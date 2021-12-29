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
* Go to [appicon.co](https://appicon.co/) and convert your `.png` file to `.ico` file

### Manual Way:

#### For Android
* Navigate to `android/app/src/main/res` and right-click on res folder and click `“reveal in Explorer”`. 
* Now delete all the **mipmap** folders in `res` folder and paste the mipmap folders from `AppIcon/android` folder which you have downloaded.

#### For iOS
* Now navigate to the `ios/Runner/Assets.xcassets`. Now after you are in Runner folder, right-click on Runner folder and click `“reveal in Explorer”`.
* Now delete the `Assets.xcassets` folder and paste the Assets.xcassets folder from `AppIcon/Assets.xcassets` which you have downloaded.

### Automatic Way
Use `flutter_launcher_icons` package.

* Add your Flutter Launcher Icons configuration to your `pubspec.yaml` or create a new config file called `flutter_launcher_icons.yaml`
```yaml
dev_dependencies:
  flutter_launcher_icons: "^0.9.2"

flutter_icons:
  android: "launcher_icon"
  ios: true
  image_path: "assets/icon/icon.png"
```
* Run the package
After setting up the configuration, all that is left to do is run the package.
```console
flutter pub get
flutter pub run flutter_launcher_icons:main
```
### Issue
```
Unhandled exception:
FormatException: Invalid number (at character 1)

pub finished with exit code 255
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


