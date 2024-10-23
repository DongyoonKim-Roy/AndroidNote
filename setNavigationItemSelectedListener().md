# setNavigationItemSelectedListener()
- This method is called on a `NavigationView`, which is typically used to create a menu of items within the navigation drawer.
- It allows us to define what should happen when a user clicks on an item from the menu.

# Example
```kt
class MainActivity : AppCompatActivity(), NavigationView.OnNavigationItemSelectedListener{
  private lateinit var binding: ActivityMainBinding

  override fun onCreate(savedInstancestate: Bundle?) {
    super.onCreate(savedInstanceState)
    binding = ActivityMainBinding.inflate(layoutInflater)
    setContentView(binding.root)

    binding.navigationDrawer.setNavigationItemSelectedListener(this)
  }
  override fun onNavigationItemSelected(item: MenuItem): Boolean {
    when (item.itemId) {
      R.id.nav_home -> {
        Toast.makeText(this, "Home", Toast.LENGTH_SHORT).show()
        return true
      }
      return false
    }
  }
}
```
- `onNavigationItemSelected`
  - It handles each menu item's click events.

# Summary
- This method is called on a `NavigationView`, which is typically used to create a menu of items within the navigation drawer.
