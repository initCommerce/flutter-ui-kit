## Changing package name

We suggest using [rename](https://pub.dev/packages/rename) to change the name and package name of the application.

First step is to run

```
pub global activate rename
```

And then you can easily change application name and package name.

```
pub global run rename --bundleId com.init.commerce.app
pub global run rename --appname "Init Commerce"
```

## Changing logo

To change the logo, Change `assets/images/logo.png` and `assets/images/logo_image.png`.

## Changing application icon

The application icon is located in `assets/icons/icon.png`, After changing the icon, You need to run command

```
flutter pub run flutter_launcher_icons:main
```

To apply changes.

## Changing appearance

You can change the theme of the application by changing the `theme` variable in `lib/config/appearance.dart` file.

```dart
final Map<String, dynamic> appearance = {
  'defaultTheme': 'light',
  'theme': {'light': purpleTheme}
};
```

The default theme is created before and you can change theme using this map.

## Error codes

Since errors are mostly related to the back-end, We have Map called errors in `config/main.dart`

This varibale maps the error codes to their error messages, Which may show up in snackbars.
