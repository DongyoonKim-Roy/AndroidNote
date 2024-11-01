# LiveData
- It is used to hold and manage observable data in a lifecycle-aware way.
- It ensures that the UI compnents only observe updates when they are in an active lifecycle state.
- It helps prevent issues like memory leaks and unnecessary UI updates.

# Key Features of LiveData
## Lifecycle Awareness
- It respects the lifecycle of the components (e.g., activities, fragments) that observe it.
- It ensures that updates are only sent when the observer is in an active state, which helps prevent crashes and memory leaks.
- Observers are automatically removed when the lifecycle owner (e.g., activities, fragments) is destroyed.

## Automatic UI Updates
- LiveData allows the UI to automatically respond to changes in the underlying data.
- When the data held by LiveData changes, all registered observers are notified, and the UI is updated accordingly.

## No Manual Lifecycle Handling
- It manages subscriptions and unsubscribing automatically based on the lifecycle state of the observer.

## Data Synchronization
- It ensures taht the UI is always synchronized with the data.
- When an observer becomes active, it receives the latest data immediately.

# Example
- **Create LiveData**
  - LiveData can be created within a `VIewModel` to hold data that the UI needs to display.
```kt
class MyViewModel : ViewModel(){
  val myData: MutableLiveData<String> = NutableLiveData()
}
```

- **Update LiveData**
  - The value of LiveData can be updated by using `setValue()` on the main thread or `postValue()` from a background thread.
```kt
myData.value = "New Value" // Used on the main thread
myData.postValue("New Value") // Used on background threads
```

- **Ovserve LiveData**
  - In an activity or fragment, you can observe LiveData to respond to changes.
```kt
myViewModel.myData.observe(this, Observer { newData ->
  textView.text = newData
})
```

- **Transformations and MediatorLiveData**
  - `Transformations` can be used to manipulate the LiveData before it is passed to the observer.
  - This is useful for data formatting or mapping.
  - `MediatorLiveData` can ovserve multiple LiveData sources and react when any of them change.
```kt
val transformedData = Transformations.map(myData) { data ->
  "Formatted $data"
}
```
```kt
val mediator = MediatorLiveData<String>()
mediator.addSource(myData) { value ->
  mediator.value = value.toUpperCase()
}
```

# Example Full Code
`MainActivity.kt`
```kt
class MainActivity : AppCompatActivity() {
    private lateinit var binding : ActivityMainBinding
    private lateinit var viewModel: ViewModel
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        viewModel = ViewModelProvider(this).get(ViewModel::class.java)

        viewModel.counterLiveData.observe(this, Observer {count->
            binding.count.text = "$count"
        })


        binding.countBtn.setOnClickListener(){
            viewModel.increment()
        }
    }
}
```

`ViewModel.kt`
```kt
class ViewModel : ViewModel() {
    private val countLiveData = MutableLiveData<Int>()

    init {
        countLiveData.value = 0
    }

    val counterLiveData: LiveData<Int>
        get() = countLiveData

    fun increment() {
        countLiveData.value = (countLiveData.value ?: 0) + 1
    }
}
```

# Summary
- `LiveData` simplifies data observation and helps build **responsive apps** by working seamlessly with Android's lifecycle management.
