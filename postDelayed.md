# postDelayed
it is a method used to schedule a `Runnable` to be executed after a specified delay. It is commonly used when you want to run a block of code after some time has passed without blocking the main thread (UI thread). This is particularly useful for tasks like delaying UI updates, animations, or navigating to a new screen after a splash screen.
In Kotlin, you can use `postDelyed` on a `Handler` or directly on a `View`.

# Example
`postDelayed` with a `Handler`
```kt
val handler = Handler(Looper.getMainLooper())
handler.postDelayed({
  println("This will run after 3 seconds")
}, 3000)
```
`postDelayed` on a `View`
```kt
button.postDelayed({
  button.text = "Text updated after 3 seconds"
}, 3000)
```
