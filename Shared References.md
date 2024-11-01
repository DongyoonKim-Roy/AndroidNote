# Shared References
- It provides a way to store simple key-value pairs of primitive data types in a private, persistent storage.
- It is a lightweight solution for stroing small amounts of data, such as user preferences, settings, or app state information.

# Purpose
- persistent Storage
  - Data stored in `SharedPreferences` remains available even after the app is closed or the device is restarted.
- Simple Data Storage
  - Best suited for small amounts of data like user settings, login status, and application preferences.
 
# Example
```kt
class MainActivity : AppCompatActivity() {
    private lateinit var binding: ActivityMainBinding
    private lateinit var sharedPreferences: SharedPreferences

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        sharedPreferences = getSharedPreferences("NoteData", Context.MODE_PRIVATE)
        binding.saveButton.setOnClickListener() {
            val note = binding.userInput.text.toString()

            val sharedEdit = sharedPreferences.edit()
            sharedEdit.putString("note", note)
            sharedEdit.apply()
            Toast.makeText(this@MainActivity, "Note Stored Successfully", Toast.LENGTH_SHORT).show()
            binding.userInput.text.clear()
        }

        binding.displayButton.setOnClickListener() {
            val storedNote = sharedPreferences.getString("note", "")
            binding.displayNote.text = "$storedNote"
        }
    }
}
```
- sharedPreferences = getSharedPreferences("NoteData", Context.MODE_PRIVATE)
  - `NoteData` : Name of the preference file. Multiple file can be created with different names.
  - `Context.MODE_PRIVATE` : Ensures that the file is **accessible only by your application**.
- val sharedEdit = sharedPreferences.edit()
  - `sharedPrefefences.edit()` : creates an instance of `SharedPreferences.Editor`.
- sharedEdit.putString("note", note) : Method to save data, (key, value). 
- sharedEdit.apply() : wirtes the changes to disk asynchronously (faster, non-blocking).

# Summary
- `SharedPreferences` is an ideal choice for **storing user prefernces and small, simple data**.
- It provides **an easy to use API for reading and writing key-value pairs** that persist across user sessions.
