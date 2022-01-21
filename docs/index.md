# E-Commerce UI kit


## Setup enviroment
This UI kit is written in Flutter so you will need Flutter SDK to run this application.

Below are steps to install Flutter SDK based on your OS.

+ [MacOS](https://docs.flutter.dev/get-started/install/macos)
+ [Linux](https://docs.flutter.dev/get-started/install/linux)
+ [Windows](https://docs.flutter.dev/get-started/install/windows)
+ [ChromeOS](https://docs.flutter.dev/get-started/install/chromeos)



## Project layout
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


## Concpets

## Creating a new page

To create a new page, first of all consider if the new page should be in already defiend modules or not. If it wasn't
then goto [Creating a new module](#Creating a new module)
![Create page](assets/create-page.jpeg)

### Create page files
Choose the module and then head into the presentation folder of it.
Create a new folder for new page and also create the files `page.dart` and `controller.dart`.

In `page.dart` add the widget and in `controller.dart` add the statemangment codes with
any package you like to use.

All you have to do is to retreive data from application layer and pump it to the widgets.

After creating the page, You have also create a route for it. The routes of pages of a module are in 
`presentation/routes.dart` file. After you created a route, You need to register the page in `MaterialApp`.

### Registering page in MaterialApp
`main.dart` file of every module contains a variable called `routes` which is used to
register the routes.
You need to add the string variable of route (which you created in previous step) in this Map and then 
map it to the page you just created.

![Module routes](assets/module-routes.png)

All routes from all modules are gathered in the MaterialApp. As you can see, It's the same for `onGeneratedRoutes`
![Material App routes](assets/material-app-routes.png)
