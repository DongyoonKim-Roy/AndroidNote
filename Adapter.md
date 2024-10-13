# Adapter
It is a bridge between the UI components (like `ListView`, `GridView`, RecyclerView`, etc.) and **the data source** that fills those UI components with content.

# Key Tasks
- Mapping data to views : Adapters **take data from a data source** (like an array, list, or database) and **convert each item in that data source into a view** that can be displayed in a UI component.
- Managing the view creation : Adapters are responsible for creating and recycling the views for the UI components efficiently.

# Types of Adapters

## ArrayAdapter
- Used to **bind an array of objects to a UI component** like `ListView` or `Spinner`.

## Example
```kt
val countries = arrayOf("Pasta", "Toast", "Taco", "Curry")
val listView = findViewById<ListView>(R.id.yourListViewId)
val adapter = ArrayAdapter(this,
 android.R.layout.simple_list_ite_1, //The layout of each item in the list
 countries)
listView.adapter = adapter
```

## SimpleAdapter
- Used to bind data from more complex data structures (like a `List<Map<String, Object>>`) to a UI component.

## Example
```kt
//Prepare data
val dataList: MutableList<Map<String, Any>> = ArrayList()
val item1: MutableMap<String, Any> = HashMap()
item1["icon"] = R.drawable.icon1
item1["text"] = "Item 1"
dataList.add(item1)

val dataList: MutableList<Map<String, Any>> = ArrayList()
val item2: MutableMap<String, Any> = HashMap()
item1["icon"] = R.drawable.icon1
item1["text"] = "Item 2"
dataList.add(item2)

val from = arrayOf("icon", "text")
val to - intArrayOf(R.id.icon, R.id.text)

val adapter = SimpleAdapter(
  this,
  dataList,
  R.layout.row_layout,
  from,
  to
)

val listView = findViewById<ListView>(R.id.yourListViewId)
listView.adapyer = adapter
```

## BaseAdapter
- It is the base class for all other adapters. It can be extended to create custom adapters when the default ones do not meet your needs.

## Example
```kt
val dataList = listOf(
 mapOf("name" to "Item 1", "description" to "Description 1"),
 mapOf("name" to "Item 2", "description" to "Description 2")
)
val from = arrayOf("name", "description")
val to = intArrayOf(R.id.textName, R.id.textDescription)

val adapter = SimpleAdapter(this, dataList, R.layout.list_item, from, to)
listView.adapter = adapter
```

## RecyclerView.Adapter
- It is used with the `RecyclerView` component. This adapter provides more flexibility and control than the `ListView` or `GridView` adapters.

  ## Example
  ```kt
  val sampleData = listOf("Apple", "Orange", "Cherry", "PineApple")
  val recyclerView: RecyclerView = findViewById(R.id.myRecyclerView)
  recyclerView.layoutManager = LinearLayoutManager(this)
  recyclerView.adapter = object : RecyclerView.Adapter<RecyclerView.ViewHolder(){
    inner class SimpleViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
     val textView: TextView = itemView.findViewById(android.R.id.text1)
    }
    override fun onBindViewHolder(holder: RecyclerView, ViewHolder, position: Int){
      val simpleViewHolder = holder as SImpleViewHolder
      simpleViewHolder.textView.text = sampleData[position]
    }
    override fun getItemCount(): Int{
     return sampleData.size
    } 
  }
  ```
