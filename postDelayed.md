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

`postDelayed` with `Button`
```kt
class MainActivity : AppCompatActivity() {
    private lateinit var binding: ActivityMainBinding

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        val handler = Handler(Looper.getMainLooper())

        binding.mainBtn.setOnClickListener {
            handler.postDelayed({
                val intent = Intent(this, secondActivity::class.java)
                startActivity(intent)
            }, 6000)
        }

        binding.secBtn.setOnClickListener() {
            val intent = Intent(this, secondActivity::class.java)
            startActivity(intent)
            finish()
        }

    }
}
```
In this example, if you click the mainBtn, 6 seconds after the secondActivity is opening.  
However, when you click the secBtn, the secondActivity is opening immediately.
