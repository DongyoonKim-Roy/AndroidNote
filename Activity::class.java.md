# Activity::class.java
In Android, `Activity:class.java` is commonly used when working with intents, especially for **explicit intents**. 
This syntax is related to Kotlin's reflection system and how it represents classes and types in Kotlin and Java interoperability.

# Breakdown of `Activity::class.java`
- `Activity` : Refers to the class name of an Android activity(`MainActivity` Or `SecondActivity`).  
  An activity is one of the fundamental components of an Android app, representing a single screen with a user interface.
- `::class` : Kotlin's syntax for obtaining a reference to a **Kotlin class**.  
  It returns a `KClass`, which represents a class in Kotlin.  
  For example, `MainActivity::class` or `SecondActivity::class` refers to the MainActivity or SecondActivity class itself.
- `.java` : is used to get the **Java class reference** (`Class<T>`), which is required for interoperability between Kotlin and Java.  
  Android's **Intent** (which is written in Java) expects a Class<T> type for the target component (like an `Activity`), so the `::class.java` converts the Kotlin class reference (`KClass`) to a Java class reference.

# Example
```
val btn = findViewById<Button>(R.id.exampleBtn)
btn.setOnClickListener(){
  val intent = Intent(this, SecondActivity::class.java)
  startActivity(intent)
  finish()
}
```
In this example :
- `this` : Refers to the current activity.
- `SecondActivity::class.java` : Refers to Java class reference for SecondActivity, wihch is passed as the target activity to be started by intent.
> For emxaple, `this`(`from`) -> `SecondActivity::class.java`(`to, target`)

# Summary
When you use `Intent` in Andorid to navigate from one activity to another, the `Intent` constructor expects a Java `Class<T>` object to specify which activity you want to start.  
  In Kotlin, classes are representd by `KClass`, but the `Intent` class is a Java class, so it requires a Java `Class<T>`.  
  Thus, to start an activity in Kotlin, you use `Activity::class.java` to get the required Java class reference.
  Think `this` is from Activity and `SecondActivity:class.java` is the to, target Activity.
  
  
