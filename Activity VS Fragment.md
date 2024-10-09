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

If see the example
