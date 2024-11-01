# MVVM (Model - View - ViewModel)
- MVVM (Model - View - ViewModel) is a software architectural pattern commonly used for developing applications, especially when building user interfaces.
- It helps organize and structure code in a way that separates concerns, making the codebase more maintainable and testable.

# Component of the MVVM pattern 
  ## Model
  - Definition
    - Represents the data and business logic of the application.
    - It is responsible for managing the data and rules of the application.
  - Functionality
    - The model can be thought of as the part of the code that handles data retrieval, storage, and business rules.
    - It is independent of the UI and provides data to the ViewModel in a format that can be easily consumed.
  ## View
  - Definition
    - The user interface (UI) of the application.
    - This is what the user interacts with.
  - Functionality
    - The view displays data to the user and captures user interactions.
    - It is typically implemented using UI frameworks.
    - The view should ideally have minimal code-behind and avoid complex logic to ensure separation of concerns.
  ## ViewModel
  - Definition
    - Serves as the intermediary between the Model and the View.
    - It acts as a bridge that facilitates communication and data binding.
  - Functionality
    - The ViewModel retrieves data from the Model and prepares it for the View.
    - It holds the logic for what should be presented in the UI and responds to user input from the View by updating the Model and/or changing the View's state.
  - Key Point
    - The ViewModel is not aware of the View, which allows for better testability and modular code.
    - Data binding is often used to connect the View and the ViewModel.
