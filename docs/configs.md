

All files related to the configuration of application are located in `lib/config/` folder.

## Changing appearance


You can change the theme of the application by changing the `theme` variable in `lib/config/appearance.dart` file.

```dart
final Map<String, dynamic> appearance = {
  'defaultTheme': 'light',
  'theme': {'light': defaultTheme}
};
```

The default theme is created before and you can change theme using this map.


## Error codes

Since errors are mostly related to the back-end, We have Map called errors in `config/main.dart`

This varibale maps the error codes to their error messages, Which may show up in snackbars.
