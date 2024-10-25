# Context
- It is an interface to global information about an application environment. It **allows access to** thing like :
  - Resources : Accessing strings, drawables, dimensions, etc.
  - System services : Such as connectivity, location, layout inflation, and more.
  - Application package : Accessing the app's package and interacting with it, like starting activities, services, or accessing braodcast receivers.

# It is important
- Resource Access : Without `Context`, we cannot access the app's resources.
- System Interaction : `Context` provides access to the Android system and its services, like launching new activities, starting services, or accessing the device's storage.
- View Inflation : Many UI-related tasks, like inflating layouts or getting a `LayoutInflater`, require a `Context`.
- Lifetime Awareness : Using the right type of context ensures we avoid memory leaks or improper behavior by tying the context's lifecycle to the correct component.

# Summary
- `Context` is a central class in Android that provies access to app resources and system services.
- There are different types of `Context` based on what component (Activity, Application, Service), and each type has specific use cases.
