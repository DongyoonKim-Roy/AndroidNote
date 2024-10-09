# Activity VS Fragment
In Android development, Fragments and Activities are both building blocks of user interfaces, but they esrve different purposes and have different behaviors.

# Activity
 It is **essentially a screen with which users** can interact, think of **it as a container for app's UI**.  
 Every app typically has multiple activities that represent different screens or sections of the app.
- An activity is a complete screen.
- It usually takes care of both the layout (UI) and the logic (Java/Kotlin code).
- It manages its own lifecycle: it can be created, started, resumed,paused, stopped, or destroyed.
- It is self-contained and doesn't typically share UI components easily with other activities.

# Fragment
**It is a reusable portion of the UI inside an activity.** 
Fragments are introduced to **allow developers to create flexible** and **reusable UI components**.
- A fragment is like a **sub-activity** or a **part of the user interface** that **exists within an activity**.
- Multiple fragments can be combined in a single activity to build dynamic and multi-pane layouts.
- Fragments can be reused across different activities, making code more modular.
- Fragments also have their own lifecycle, which is closely tied to the activity they are part of.
- They can be added or removed from an activity while the activity is running, making them useful for dynamic UIs.

# Example
## Activity
![frag1](https://github.com/user-attachments/assets/7dd86113-f679-4021-8381-a1febc4000e6)

## Fragment
![frag2](https://github.com/user-attachments/assets/cd7dda19-a5b8-4367-94ff-2d0c32a68970)

The example might not be perfect, but I’ll try my best to explain the difference between them.  

In the example, there are two buttons in an Activity. When you click one of the buttons, it navigates to a second Activity, which shows the same buttons. The goal is to change the text displayed on the screen, like 'Main Activity' or 'Second Activity,' after clicking the buttons.  

Using Activities for this setup means creating multiple buttons and Activities, which can consume more memory, especially as the app grows.  

In contrast, with Fragments, the same two buttons can be reused, and only the text needs to be updated. This approach is more efficient because Fragments allow for changing views within a single Activity, reducing memory usage.  


# Code
build.gralde.kts
```kts
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.kotlin.android)
}

android {
    namespace = "com.example.fragandacti"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.example.fragandacti"
        minSdk = 24
        targetSdk = 34
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
    kotlinOptions {
        jvmTarget = "1.8"
    }
    viewBinding {
        enable = true
    }
}
```
`viewBinding` is added because
 - `viewBinding` automatically generates a binding class based on layout files, so view can be directly accessed by calling their IDs. No need `findViewById()`.
 - it ensures that you are working with views that actually exist in your layout. Therefore, it can be **type safety**.
 - It helps handle nullability more safely by ensuring you clean up refernces to the view when the fragment's view is destroyed, **preventing memory leak**.
