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

### Style and Theme Resources (`res/values/styles.xml`)
- Defines themes and styles to apply consistent appearance (like font sizes, and colors) across difeerent views or activities.

### Example
```xml
<resources>
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
        <item name="colorPrimary">@color/primary_color</item>
        <item name="colorAccent">@color/personal_color</item>
    </style>
</resources>
```

### Menu Resources (`res/menu`)
- Defines the contents of menus and toolbars in XML

### Example
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/action_settings"
          android:title="@string/settings"
          android:icon="@drawable/ic_settings"/>
</menu>
```

# Manifest XML (AndroidManifest.xml)
- `AndroidManifest.xml` file is a critical configuration file that **declares essential information** about the app to the Android system.
  It must be included in every Android project.
- It is located at the root of the `app/src/main/` directory.
- Roles :
  - Defines the app's **package name**.
  - Lists all **activities, services, receivers,** and **content providers**.
  - Specifies **permissions** the app requires (e.g., accessing the camera, internet).
  - Declares the **app's entry point** (the `MainActivity or launcher activity).
  - Defines hardware and software features the app needs (e.g., camera, Bluetooth).

## Package Declaration
- Defines the unique package name for the application.
## Example
```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">
```
- The `package` attribute **uniquely identifies** the app **on the Play Store** and **on the device**.

## Application Declaration
- Defines the global properties of the application, including icons, themes, and whether it supports multiple processes.
## Example
```xml
<application
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:theme="@style/AppTheme">
```
- `android:icon` sets the app's launcher icon.
- `android:label` specifies the app name.
- `android:theme` applies a global theme to the app, usually defined in `res/values/styles.xml`.

## Activity Declaration (Launcher Activity)
- Declares activities (screens) that the app contains. One activity must be declared as the entry point for the app (the **Launcher**).
## Example
```xml
<activity android:name=".MainActivity">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```
- `android:name` specifies the activity class (e.g., MainActivity) that this entry refers to.
- `intent-filter`
    - `android.intent.action.MAIN` (**Action**) declares this as the main entry point.
    - `android.intent.category.LAUNCHER` (**Category**) makes the activity the app's launcher activity, meaning it appears on the app drawer.

## Service Declaration
- Declares a service that runs in the background to perform long-running operations.
## Example
```xml
<service android:name=".MyBackgroundService"
         android:enabled="true"
         android:exported="false"/>
```
- `android:name` is the name of the service class.
- `android:enabled` defines whether the service is enabled (default is **`true`**)
- `android:exported` controls whether otehr apps can interact with this service (use `false` if only your app should).

## Broadcast Receiver Declaration
- Declares a broadcast receiver that listens for system-wide broadcast announcements.
## Example
```xml
<receiver android:name=".MyReceiver">
    <intent-filter>
        <action android:name="android.intent.action.BOOT_COMPLETED" />
    </intent-filter>
</receiver>
```
- `android:name` defines the broadcast receiver class.
- `intent-filter` specifies which broadcasts it listens to, such as `BOOT_COMPLETED` (sent when the device finishes booting up).

## Content Provider Declaration
- Declares a content provider that manages shared data between applications.
## Example
```xml
<provider
    android:name=".MyContentProvider"
    android:authorities="com.example.myapp.provider"
    android:exported="true"/>
```
- `android:name` is implementing the content provider.
- `android:authorities` is a unique name to identify the provider.
- `android:exported` is whether** other apps can access** this content provider (use `false` to **restrict access to the app only**).

## Permission Declaration
- Defines what permissions the app needs to function properly, such as access to the camera, storage, or internet.
## Example
```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```
- `android:name` specifies the system permissions the app needs to run.
    - `CAMERA` requried to use the device's camera.
    - `INTERNET` allows the app to access the internet.
    - `ACCESS_FINE_LOCATION` allows the app to access precise location data. 

## Hardware and Software Features
- defines actions and categories for implicit intents (used when the app can respond to an intent even without specifying the app's class name).
## Example
```xml
<uses-feature android:name="android.hardware.camera" android:required="true"/>
<uses-feature android:name="android.hardware.bluetooth_le" android:required="false"/>
```
- `android:name` specifies the feature (e.g., camera or Bluetooth).
- `android:required` If `true`, the app won't be available on devices without this feature. If `false` the app **can still run on devices** that don't have this feature **but may provide limited functionality**.

## Intent Filters (for implicit intents)
- declares the hardware and software features that the app requries or supports, such as Bluetooth, NFC, or a camera.
## Example
```xml
<activity android:name=".ShareActivity">
    <intent-filter>
        <action android:name="android.intent.action.SEND" />
        <category android:name="android.intent.category.DEFAULT" />
        <data android:mimeType="text/plain" />
    </intent-filter>
</activity>
```
- `action` is type of action (like `SEND` to share content.
- `category` defines what type of action it belongs to (usually `DEFAULT` for general actions).
- `data` defines the type of data (e.g., `text/plain` to send plain text).

## Meta-data Tag
- provides additional information about the app or specific components using a key-value pair.
## Example
```xml
<meta-data
    android:name="com.example.analytics.API_KEY"
    android:value="your-api-key-here"/>
```
- `android:name` is the key for the metadata.
- `android:value` is the value for the metadata. This could be API keys, configuration settings, etc.

## Application Features (e.g., MultiDex)
- declares special application features such as MultiDex (used for large apps that require multiple dex files). 
## Example
```xml
<application
    android:name="android.support.multidex.MultiDexApplication"
    android:allowBackup="true">
```
- `android:name` specifies the application class or feature (like enabling MultiDex).
- `android:allowBackup` determines whether the app's data can be backed up.

# Example of Full AndroidManifest.xml
```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">

    <!-- Permissions -->
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.INTERNET" />

    <!-- Features -->
    <uses-feature android:name="android.hardware.camera" android:required="true" />

    <!-- Application block -->
    <application
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme">

        <!-- MainActivity (Launcher) -->
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- Additional activities -->
        <activity android:name=".ShareActivity">
            <intent-filter>
                <action android:name="android.intent.action.SEND" />
                <category android:name="android.intent.category.DEFAULT" />
                <data android:mimeType="text/plain" />
            </intent-filter>
        </activity>

        <!-- Service -->
        <service android:name=".MyBackgroundService"
                 android:enabled="true"
                 android:exported="false"/>

        <!-- Broadcast Receiver -->
        <receiver android:name=".MyReceiver">
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
            </intent-filter>
        </receiver>

        <!-- Content Provider -->
        <provider
            android:name=".MyContentProvider"
            android:authorities="com.example.myapp.provider"
            android:exported="true"/>

    </application>
</manifest>
```
> More specific example of them is coming later.
