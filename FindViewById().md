# FindViewById()
`findViewById()` is a method used to retrieve a reference to a **view** object in the current layout. This allows you to access and manipulate UI elements (like **Button**, **TextView**, **ImageVIew**, etc.). The method searches the view hierarchy for a view iwth the specified ID and returns the view if found.


# Difference between `val btn : Button = findViewById(R.id.btnId)` and `val btn = findViewById<Button>(R.id.btnId)`


## `val button: Button = findViewById(R.id.btnId)`
The variable `button` is explicitly declared as type `Button`.  
It's telling Kotlin that the result of `findViewById()` should be treated as a `Button`, even though the return type of `findViewById()` is a generic `View`.  
Because of that, **type casting** will happen internally.  
It is needed because before **API level 26 (Android 8.0)**, `findViewById()` **returns a generic** `View` object, so **you needed to case it to the appropriate view type** like `Button`, `TextView`, etc.  
## Example
```
val btn: Button = findViewById(R.id.btnid) as Button
```

## `val btn = findViewById<Button>(R.id.btnId)`
This is a more modern and simpler approach, introduced in **API level 26 (Android 8.0)** and later.  
The method `findViewById()` is now **generic** and can return a specific type of view without requiring explicit casting.  
Since `findViewById()` is generic, it specifies the type of view you expect (in this case, `Button`), and the compiler automatically knows that the returned type is `Button`.  


# Which one is better?
`val button = findViewById<Button>(R.id.btnId)` is better. It is because  
- It is **safer** because you specify the expected view type, and the compiler will check that the cast is correct. This prevents potential `ClassCastException` errors at runtime.

# Key Differencese
| **Aspect ** | `val btn: Button = findViewById(R.id.myButton)` | `val btn = findViewById<Button>(R.id.btnId)` |
|  :----------: | :----------: | :----------: |
| **Type declaration** | Explicit (`Button`) | Inferred by the compiler |
| **Explicit casting** | Needed before API 26 | Not required, even before API 26 |
| **Ease of use** | Slightly verbose due to the type declaration | More concies and cleaner |
| **Runtime safety** | Requries careful casting to avoid exceptions | Safer and type-checked at compile time |
| Version compatibility | Used before API 26 when `findViewById()` wasn't generic | Ideal for API 26+ (with generic `findViewById()`) |
| Readability | A bit less readable due to type declaration | More readable wit cleaner syntax |

# Summary
- Before API 26 : `findViewById()` returns `View`, so it requires type cast, `val btn: Button = findViewById(R.id.btnId) as Button`.
- API 26+ : Since `findViewById()` becomes generic method, type cast is not requried, `val btn = findViewById<Button>(R.id.btnId)`.
In Modern Android, the **second form** is **preferred** for its **simplicity** and **compile-time safety**.
