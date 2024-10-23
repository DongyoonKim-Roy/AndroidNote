# supportFragmentManager
- It give access to the `FragmentManager` that manages **fragments** in an activity that uses AndroidX's support library for backward compatibility.


# example
```kt
val fragmentManager = supportFragmentManager
val fragmentTransaction = fragmentManager.beginTransaction()
val fragment = MyFragment()
fragmentTransaction.replace(R.id.fragment_container, fragment)
fragmentTransaction.commit()
```
- `supportFragmentManager` : It gives access to the `FragmentManager` for managing fragments within actiivty.
- `beginTransaction()` : It initiates a `FragmentTransaction` which allows us to perform actions like adding, removing, or replacing fragments.
- `replace()` : It is used to replace a container (such as a `FrameLayout` in layout file) with the fragment.
- `commit()` : FInalizes and applies the fragment transaction.

# Summary
- `supportFragmentManager` is crucial component for managing fragments in Android, especially when we are using the AndroidX support libraries for backward compatibility.
