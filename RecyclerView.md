# RecyclerView
- It is **flexible** and efficient view for displaying a large set of data in Android development.

# Key Features
- View Recycling :
  - It helps in efficient memory usage.
  - It reuses item views that have scrolled out of visibility and re-binds them with new data, reducing the need to create new views repeatedly.
- Layout Managers :
  - It defines how items are arranged on the screen.
  - `LinearLayoutManager` arranges items in a vertical or horizontal scrolling list.
- Adapters :
  - A `RecyclerView.Adapter` binds the data to the views displayed within the `RecyclerView`.
  - It acts as a bridge between the data source and the `RecyclerView`.
- ViewHolder Pattern :
  - `RecyclerView` enforces the use of a `ViewHolder` pattern to improve performnace.
  - The `ViewHolder` class holds the views for each item and helps reduce unnecessary `findViewById()` calls during binding.

# Basic Structure (Example Code)
activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/recyclerView"
        android:layout_width="409dp"
        android:layout_height="729dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:listitem="@layout/recycler_view_item" />

</RelativeLayout>
```

recycler_view_item.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <androidx.cardview.widget.CardView
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <TextView
                android:id="@+id/title"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:hint="title"
                android:textSize="20sp" />

            <TextView
                android:id="@+id/description"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:hint="description"
                android:textSize="20sp" />
        </LinearLayout>
    </androidx.cardview.widget.CardView>

</RelativeLayout>
```

Adapter.kt
```kt
package com.example.longpressprac.Adapter

import android.content.Context
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView
import androidx.recyclerview.widget.RecyclerView
import com.example.longpressprac.Model.ExampleItem
import com.example.longpressprac.R
import org.w3c.dom.Text

class Adapter(context: Context, private var items: MutableList<ExampleItem>) :
    RecyclerView.Adapter<Adapter.ViewHolder>() {

    class ViewHolder(view: View) : RecyclerView.ViewHolder(view) {
        val title: TextView = view.findViewById(R.id.title)
        val description: TextView = view.findViewById(R.id.description)
    }

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val view =
            LayoutInflater.from(parent.context).inflate(R.layout.recycler_view_item, parent, false)
        return ViewHolder(view)
    }

    override fun getItemCount(): Int = items.size

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        val currItem = items[position]
        holder.title.text = currItem.title
        holder.description.text = currItem.description
    }
}
```

ExampleItem.kt
```kt
package com.example.longpressprac.Model

data class ExampleItem(val title: String, val description: String){

}
```
