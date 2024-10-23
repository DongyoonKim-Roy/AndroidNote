# ActionBarDrawerToggle
- It helps to manage the interaction between an `ActionBar` (or toolbar) and a navigation drawer.
- It provides an easy way to synchronize the state of the navigation drawer with the `ActionBar`.
- It works on **Navigation Drawer**, and **ActionBar** (or **Toolbar**).

# Main Features
- Hamburger Icon :
  - It displays the hanburger icon in the toolbar.
- Synchronizes Drawer and Toolbar :
  - It automatically listens for changes to the navigation drawer (opened/closed) and updates the toolbar icon accordingly.
- Drawer Listener :
  - It listens to gestures or clicks on the drawer, triggering the open and close actions appropriately.

# Key Methods
- `syncState()` :
  - Syncs the state of the drawer toggle with the current state of the navigation drawer.
  - It ensures that the toolbar icon shows the correct icon (hamburger or back arrow).
- `onDrawerOpened()` :
  - Called when the navigation drawer is opened.
- `onDrawerClosed()` :
  - Called when the navigation drawer is closed.
- `onDrawerSlide()` :
  - Called when the user is interacting with the navigation drawer, often used for animations during the drawer's sliding.

# Example
```kt
val drawerLayout: DrawerLayout = findViewById(R.id.drawer_layout)
val toolbar: Toolbar = findViewById(R.id.toolbar)

val toggle = ActionBarDrawerToggle(
    this,                  // Activity hosting the drawer
    drawerLayout,          // DrawerLayout instance
    toolbar,               // Toolbar instance
    R.string.drawer_open,  // "open drawer" description
    R.string.drawer_close  // "close drawer" description
)
drawerLayout.addDrawerListener(toggle)
toggle.syncState()
supportActionBar?.setDisplayHomeAsUpEnabled(true)
```

# Summary
- `ActionBarDrawerToggle` helps to manage the interaction between an `ActionBar` or toolbar and a navigation drawer.
- It provides an easy way to synchronize the state of the navigation drawer with the `ActionBar`.
