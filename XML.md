# XML (Extensible Markup Language)
In Android development, XML is widely used for defining the user **interface**, **resources**, and other components in structured, hierarchical way.  
It is a key part of Android app devlopment because it helps to separate the presentation (UI) from the logic (Java/Kotlin code).  
It is sotred in the `res/layout` folder.

# Layout XML Files (UI Layouts)
- XML is used to define the **structure and appearance** of the user interface, such as where buttons, text fields, images, and other elements are placed on the screen.
- Common XML Elements are `TextView`, `BUtton`, `ImageVIew`, `LinearLayout`, `ConstraintLayout`, and `RecyclerView`.

# Examlple
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/explicitButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Explicit Intent"
        android:textAllCaps="true"
        android:layout_marginVertical="400dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
> [Difference Between <Button /> and <Button></Button>](), [layout]()

# Resource XML Files
**Resource files** are non-code assets that your app uses, such as colors, strings, images, and dimensions. There are stored in various subfolders within the `res/` directory.

## Types of Resorce XMLs

### String Resource (`res/values/strings.xml`)
- Stores text strings, typically used for internationalization (i.e., supporting different laguages).

### Example
```xml
<resources>
    <string name="app_name">My App</string>
    <string name="btn_string">Custom Button</string>
</resources>
```

### Color Resources (`res/values/colors.xml`)
-Defines colors that can be reused throghout the app.

### Example
```xml
<resources>
    <color name="primary_color">#6200EE</color>
    <color name="personal_color">#62100ff</color>
</resources>
```

### Dimens Resources (`res/values/dimens.xml`)
- Stores dimension values (e.g., padding, margins) to maintain consistency across the app.

### Example
```xml
    <dimen name="default_padding">10dp</dimen>
    <dimen name="default_text_size">12sp</dimen>
```
