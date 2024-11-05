# Coroutines
- They provide an efficient way to manage background threads and simplify asynchronous programming in Android development.
- Coroutines are lightweight threads that allow us to perform asynchronous and non-blocking operations in a structured and more readable way.
- They enable concurrecny within a program without needing to manually manage threads.

# Why Use Coroutines?
**Avoid Blocking the Main Thread**
- Long-running tasks can cause the UI to become unresponsive if run on the main thread.
- Coroutines make it easy to move these tasks off the main thread and run them asynchronously.

**Simplified Asynchronous Code**
- Coroutines allow us to write asynchronous code that is sequential and easy to read, as opposed to the callback-based approach.

**Structured Concurrency**
- Coroutines proved tools for structured concurrency, ensuring that operations are completed in a predictable manner and are properly cleaned up.

# Example
```kt
binding.countBtn.setOnclickListener {
  binding.countNumber.text = counter++.toString()
}

binding.downloadBtn.setOnClickListener {
  CoroutineScope(Dispatchers.IO).launch {
    for(i in 1..1000) {
      Log.i("TAG", "Downloading $i in ${Thread.currentTHread().name}")
    }
  }
}
```
- When countBtn is clicked, the count will be increased.
- When dowloadBtn is clicked, "Downloading i" will display.
- When download is in progress, countBtn will increase the count.

# Summary
- Coroutines provide a powerful tool for managing background tasks, improving app performance and keeping the UI responsive.
