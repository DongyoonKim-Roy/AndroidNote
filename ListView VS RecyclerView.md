# ListView VS RecyclerView
Both `ListView` and `RecyclerView` are used to display lists of data in Android, but they have key differences in terms of performance, flexibility, and features.

# ListView
- An older UI component used to display a list of items in a **verically scrollable layout**.
- **Simpler but less flexible** and performant compared to `RecyclerView`.

# RecyclerView
- It is more powerful and **flexible** replacemnet for `ListView`
- It offers **more control over the layout, animations, and handling of large datasets** with better memory management.

# Performance
## ListView
-Recycling is manual, requiring developers to check whether a `convertView` is available to reuse.

## Example
```kt
override fun getView(position: Int, convertView: View?, parent: ViewGroup): View{
  var view = convertView
  if (view == null){
    view = LayoutInflater.from(context).inflate(R.layour.list_item, parent, false)
  }

  return view!! //Non-null Assertion
}
```
- `convertView` : In a `ListView`, as the user scrolls, the system only keeps a limited number of item views in memory, rather than creating a new view for each item in the list.
  To avoid creating a new view each time, the `ListView` tries to **reuse** old views (which are no longer visible on the screen) through the `convertView` parameter.
