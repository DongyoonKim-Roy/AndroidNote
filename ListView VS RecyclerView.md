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
- Recycling is manual, requiring developers to check whether a `convertView` is available to reuse.

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

## RecylerView
- Implements a more efficient view recycling system via `ViewHolder` pattern by default. It handles view recycling and re-binding more efficiently, especially for alrge lists, which improves performance significantly.
- VieHolder pattern is mandatory, leading to better organization and performance.

```kt
class customAdapter: RecyclerView.Adapter<customAdapter.MyViewHolder>(){
  class MyViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView){
    //initialize views here
  }

  override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): MyViewHolder {
    val view = LayoutInflater.from(parent.context).inflate(R.layout.list_item, parent, false)
    return MyViewHolder(view)
  }

  override fun onBindViewHolder(holder: MyViewHolder, position: Int){
    //Bind data to views
  }  

  override fun getItemCount(): Int = dataList.size
}
```

# Layout Management

## ListView
- Limited to a **vertical scrolling list**. It only supports a single column list and doesn't allow much flexibility in terms of layout customization.

## RecyclerView
- Upoorts multiple **layout managers**, providing much more flexibility
  - LinearLayoutManager : For vertical or horizontal lists (similar to ListView but more powerful).
  - GridLayoutManager : For displaying items in a grid.
  - StaggeredGridLayoutManager : For creating staggered grids
- Custom layout managers can be created for more complex use cases.

# ViewHolder Pattern

## ListView
- The `ViewHolder` pattern is **optional**, though it is recommended for performance reasons. Without it, `ListView` can re-bind views unnecessarily, causing slower performance.
- `ViewHolder` needs to be manually implemented.

## RecyclerView
- The `ViwHolder` pattern is **mandatory**, which ensures efficient view recycling and better performance.
- The `ViewHolder` class is automatically used to cache views, making the scrolling smoother, especially for large datasets.
