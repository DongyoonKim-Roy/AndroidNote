# Handler
- A `Handler` is part of Android's concurrency model and is **typically used for scheduling and executing messages or runnable code at a future point in time**.  
- It allows a thread to send and process **Message** and **Runnable** objects that are associated with a thread's **MessageQueue**.
- Communication between threads : UI updates must be done on the **main (UI) thread**. However, background tasks like network calls or heavy computations are done on backgroun threads. A `Handler`** helps pass messages from a background thread to the main thread to update the UI safely**.
- Schedulint tasks : `Handler` can be used to post delayed or repated tasks. THis is useful for tasks that should e executed after some time (e.g., animations, periodic updates).

# How a Handler works
`Handler` is associated with a **Looper** which manages the `MessageQueue` of the thread. The Looper constantly processes messages in the queue and executes them on the associated thread.
- Looper : Prepares a thread to run an event loop.
- MessageQueue : Stores messages and runnables to be processed.
- Handler : Posts messages or runnables to the MessageQueue.

# Example
```kt
val handler = Handler(Looper.getMainLooper())
handler.postDelayed({
  textView.text = "Updated!"
}, 3000)
```

```kt
class MainActivity : AppCompatActivity() {
    private lateinit var binding: ActivityMainBinding
    private lateinit var textView: TextView
    private val handler = Handler(Looper.getMainLooper()) { msg ->
        when (msg.what) {
            1 -> {
                // Update UI safely on the main thread
                textView.text = "Task Completed : Result is ${msg.arg1}"
                true
            }
            else -> false
        }
    }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)
        textView = binding.mainText  // Initialize after setContentView

        // Start a background thread to simulate some work
        Thread {
            var result = 0
            for (i in 1..5) {
                Thread.sleep(1000) // Simulate work
                result += i
            }

            // Pass result to the handler (on the main thread)
            val message = Message.obtain().apply {
                what = 1
                arg1 = result
            }
            handler.sendMessage(message)
        }.start()
    }
}
```

# Summary
- `Handler` allows a tread to send and process **Message** and **Runnable** objects that are associated with a thread's **MessageQueue**.
- Communication between threads : UI updates must be done on the **main (UI) thread**. However, background tasks like network calls or heavy computations are done on backgroun threads. A `Handler`** helps pass messages from a background thread to the main thread to update the UI safely**.
