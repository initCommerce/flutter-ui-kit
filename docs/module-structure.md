# Modules

The modules are an implementation of Domain-Driven-Design in flutter.

This architecture will help you to maintain project more easily and add features without manipulating old codes.

The modules are designed in a way that you can completely remove or add them.

## Main View

Every Module should use this format

```tree
my_module
    ├── application
    │
    ├── domain
    │   │── entity
    │   └── interface
    │
    ├── infrastructure
    │   ├── model
    │   ├── provider
    │   └── repository
    │
    ├── presentation
    │   ├── page
    │   ├── widgets
    │   └── routes.dart
    │
    ├── injections.dart
    ├── api.dart
    └── main.dart
```

## Sections

### Application

This folder has the classes implemented with facade pattern.
These classes always have a `Service` suffix. for example `SearchService` and `AuthService`.

A service uses repositories and act as an interface between infrastructre and presentation.

### Domain

The domain folder contains the shared models used in the presentation and infrastructure.

#### Entity

Entity folder is used specially for classes with unique id. The entity classes will be used directly in the presentation layer and they will be extended in infrastructure so providers can use them.

#### Interface

Interfaces will help you to correctly implement application and infrastructre layers

### Infrastructure

The root of data is here. This layer is the lowest layer in the module and contains providers to connect with different data sources such as server api, google api, local storage functionallities and etc.

#### Model

Model folder will be a place to put extended models from domanin and add extra method (like json serialization) so providers can use them

#### Provider

Our provider will support us with data from servers and other data sources. This folder may contains multiple classes to access data.

#### Repository

Providers will be used in this layer and we gather them togheter. this class can only be access by application layer.

### Presentation

The UI of app will be located here, also this folder should contain a `routes.dart` which determine name of our routes.

### injections.dart

This file contains a method to register dependecies in memory using the `get_it` service locator. classes like providers, repositories, services and presenetion state notifier can be registered in memory from this method.
eg:

```dart
Future<void> registerDependencies() async {
  // Repository
  serviceLocator.registerLazySingleton<ProductRepository>(
    () => ProductRepository(
      localProductProvider: serviceLocator(),
      remoteProductProvider: serviceLocator(),
    ),
  );

  //Providers
  serviceLocator.registerLazySingleton<LocalProductProvider>(
    () => const LocalProductProvider(),
  );
  serviceLocator.registerLazySingleton<RemoteProductProvider>(
    () => const RemoteProductProvider(),
  );

}
```

### api.dart

Api class will help you connect modules togheter and use this module functionallities in other modules.

```dart
class SearchApi {
  List<Product> searchForKeyword(String keyword) {
    // code
  }
}
```

### main.dart

As you can from it's name, it's the main class of this module which represents this module in one single class and other classes can only have access to this file.

This class contains a api from previous `api.dart`, a list of routes so they can be registered in material app and also a initial route that determine what is the start point of this module.
