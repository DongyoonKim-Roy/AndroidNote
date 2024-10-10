# SplashScreen
Splash Screen or Splash View is the initial screen that appears when an app is launched. Its primary purpose is to display a brief introductory graphic, logo, or brand message while the app is loading in the background.
![splash](https://github.com/user-attachments/assets/cad57f35-bb0d-42ca-840c-f2e8425e49c7)

# Key Characteristics of a Good Splash View
- Simple Design
  - It should be clean and minimal, forten featuring just a logo or app name. Too much information can negatively impact the experience.
- Brief Duration
  - It should only last for a few seconds - long enough to load the app's initial resources. If it takes too long, it can frustrate users.
- Smooth Transition
  - After the splash screen, the app should smoothly transition to the main screnn or content.

# Downsides of Splash View
- Unnecessary Wait Time.
- Overuse of Branding.

# Code
build.gradle.kts
```kts
dependencies {

    implementation(libs.androidx.core.ktx)
    implementation(libs.androidx.appcompat)
    implementation(libs.material)
    implementation(libs.androidx.activity)
    implementation(libs.androidx.constraintlayout)
    testImplementation(libs.junit)
    androidTestImplementation(libs.androidx.junit)
    androidTestImplementation(libs.androidx.espresso.core)
    implementation("androidx.core:core-splashscreen:1.0.1")
}
```
`implementation("androidx.core:core-splashscreen:1.0.1")` is added to use splash screen.

theme.xml
```xml
    <style name="Base.Theme.Roy" parent="Theme.Material3.DayNight.NoActionBar">
        <!-- Customize your light theme here. -->
        <!-- <item name="colorPrimary">@color/my_light_primary</item> -->
    </style>

    <style name="Theme.Roy" parent="Base.Theme.Roy" />

    <style name="Theme.App.SplashScreen" parent="Theme.SplashScreen">
        <item name="windowSplashScreenBackground">@color/backColor</item>
        <item name="windowSplashScreenAnimatedIcon">@drawable/roylogo</item>
        <item name="postSplashScreenTheme">@style/Base.Theme.Roy</item>
    </style>
```
`<style name="Theme.App.SplashScreen" parent="Theme.SplashScreen"> ... </style>` is added.
  - `<item name="windowSplashScreenBackground">@color/logo</item>` is for background color.
  - `<item name="windowSplashScreenAnimatedIcon">@drawable/roylogo</item>` is a logo.
  - `<item name="postSplashScreenTheme">@style/Base.Theme.Roy</item>` refers to the theme that will be applied **after the splash screen has finished displaying**. The name of the theme will be applied is `@style/Base.Theme.Roy`.

AndroidManifest.xml
```xml
  <activity
            android:name=".MainActivity"
            android:theme="@style/Theme.App.SplashScreen"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
```
`android:theme="@style/Theme.App.SplashScreen"` is added. It is used to apply a specific theme to an activity or part of the app. In this case, it is applying the theme for the splash screen of the app.

MainActivity.kt
```kt
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        Thread.sleep(3000)
        installSplashScreen()
        setContentView(R.layout.activity_main)
    }
```
`Thread.sleep(3000)` and `installSplashScreen()` are added.
- `Thread.sleep(3000)` delays the execution of the current thread for a specified amount of time. In this case `3000` **milliseconds** which is **3 seconds**.
- `installSplashScreen` is used to install a default splash screen for an app. it handles the display of the splash screen automatically while an app is launching before transitioning to main content.
    
# Summary
- Splash Screen or Splash View is the **initial screen that appears when an app is launched**.
