
## Project structure

The architecture of this project is an inspiration from domain driven design so you can easily maintain and develop it.

```dart
    lib/
        main.dart
        helpers/
        config/
        common/
        modules/
            auth/
            home/
            search/
            cart/
            profile/
```

### helpers

The helpers folder consist of a set of tools including error handler, snackbar service and etc.

### config

Config folder just like it's name has the project configuration including it's theme, back-end address and other configs.

### common

Basically common folder is used to create common classes between modules. You can find common widgets, mixins
and other stuff in this folder.

### modules

This folder contains the sub-domains or modules of this application. We created different modules to seperate application
different sections. For example the `auth` module is only responsible for authenticating users.

A basic structure of a module is

```
moduleName/
    main.dart           # main file of module
    injections.dart     # dependency injections
    api.dart            # an api to work with other modules
    domain/
        entity/         # shared models
        interface/      # interfaces for other classes

    infrastructre/      # where the data comes in
        provider/       # data sources for application
        model/          # extended entities to work with providers
        repository/     # where we use data sources and gather them in one class

    application/        # the classes with facade pattern which
                          uses repositories in infrastructre

    presentation/       # pages of the modules
        pageName/
            page.dart
            controller.dart

```

This structure helps you to develop and maintain codes much more easily. The modules are created in a way that you can
completely remove them from the project or add a new one. Also some modules are depended to each other, for example the `home` module
needs

