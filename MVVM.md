# MVVM (Model - View - ViewModel)
- MVVM is commonly used for developing applications, especially when building user interfaces.
- It helps organize and structures code in a way that separates concerns, making the codebase more maintainable and testable.

# Model
- It **represents the data and business logic** of the application.
- It is responsible for **managing the data and rules** of the application.
- It provides data to the ViewModel in a format that can be easily consumed.

# View
- It is **UI of the application** what users interact with.
- It **displays data** to the user and **captures user interactions**.

# ViewModel
- It **retrieves data from the Model and prepares it for the View**.
- It **holds the logic for what should be presented in the UI** and **responds to user input from the View by updating the Model and/or changing the View's state**.

# Example
![스크린샷 2024-11-04 090437](https://github.com/user-attachments/assets/86b81a6a-6ebd-4894-9247-16c11771b2b5)

`CalculatorData.kt`
```kt
data class CalculatorData(val num1: Int, val num2: Int, val sum: Int) 
```

`CalculatorViewModel.kt`
```kt
CalculatorViewModel : ViewMode(){
  fun calculateSum(num1: Int, num2: Int): CalculatorData{
    val sum = num1 + num2
    return CalculatorData(num1, num2, sum)
  }
}
```
- By returing CalculatorData(num1, num2, sum), it encapsulate the input and result data in a single object.
- This makes it easier to manage and pass around data, if the data needs to be displayed or processed further in the UI or another component.
- Using a specific data class makes the return type clear and structured.

`MainActivity.kt`
```kt
class MainActivity : AppCompatActivity() {
  private lateinit var binding: ActivityMainBinding
  private lateinit var calculatorViewModel : CalculatorViewModel
  override fun onCreate(savedInstanceState: Bundle?){
    super.onCreate(savedInstanceState)
    binding = ActivityMainBinding.inflater(layoutInflater)
    setContentView(binding.root)

    calculatorViewModel = ViewModelProvider(this).get(CalculatorViewModel::class.java)
    binding.calBtn.setOnClickListener(){
      val num1 = binding.sum1.text.toString().toIntOrNull() ?: 0
      val num2 = binding.sum2.text.toString().toIntOrNull() ?: 0
      val res = calculatorViewModel.calculaterSum(num1, num2)

      binding.result.text = "${res.sum}"
    }
  }
}
```

# Summary
- This parttern helps organize and structure code in a way that separates concerns, making the codebase more maintainable and testable.
