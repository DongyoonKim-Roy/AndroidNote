# R.id
In Android, `R.id` is reference to the unique ID associated with a UI element defiend in your XML layout files. There IDs allow you to access and manipulate the UI elements programmatically in your code, such as in `findViewById()`.

# Breakdown of `R.id`
## R class
The `R` class is a **generated class** that holds references to all the resouces in your Android project. It contains nested classes representing different resource types, such as
- `R.layout` : Refers to layout XML files (e.g., `R.layout.activity_main`).
- `R.drawable` : Refers to drawable resources like **images** (e.g., `R.drawable.icon`).
- `R.id` : Refers to the IDs assigned to UI components in XML layouts (e.g., `R.id.buttonId`).

## R.id
The `R.id` is a **nested class inside the `R` class** that contains IDs for each UI element (like `Button`, `TextView`, `RecyclerView`, etc.) defined in your layout files. When you assign an ID to a view in XML using the `android:id` attribute, it creates a constant in `R.id`.

# Example
## XML
```
<Button
  android:id="@+id/submitBtn"
  android:layout_width="wrap_content"
  android:layout_height=:wrap_content"
  android:text="submit" />
```
## Kotlin
```
val button = findViewById<Button>(R.id.submitBtn)
button.setOnclickListener(){
  //handle btn click action.
}
```
>[findViewById<Button>](https://github.com/DongyoonKim-Roy/AndroidNote/blob/main/FindViewById%3C%3E.md)

# Summary
`R.id` is a part of the auto-generated `R` class that contains references to the IDs of UI elements defined in your XML layout files. `findViewById()` is used with these IDs to get a reference to the views in your code so the app can interact with them programmatically.
