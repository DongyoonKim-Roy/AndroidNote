# val VS var
In Kotlin, `val` and `var` are two ways to declare variables, but they have an important distinction in terms of **mutability** (whether the variable's value can be changed or not).


# val (Immutable variable)
## Definition  
- `val` is used to declare a `read-only` or `immutable` variable.
- Once a value is assigned to a `val` variable, it **cannot be reassigned**.  
  However, the object it refers to can still be mutable.
- It makes the code safer and easier to reason about.

## Example
```kt
//This will cause an error.
val name = "Jungle"
name = "NoJungle"

//This won't cause an error.
val list = mutableListOf(1, 2, 3)
list.add(4)
```

# var (Mutable variable)
## Definition  
- `var` is used to declare a `mutable` variable.
- The value of `var` can be changed after it has been initialized.

## Example
```kt
var name = "Jungle"
name = "NoJungle"
```

# Key Differences  
| **Aspect** | `val` | `var` |
| :----------: | :----------: | :----------: |
| **Mutability** | **Immutable** (**Read-only**), cannot be reassigned. | **Mutable**, can be reassigned. |
| **Reassignment allowed** | No | Yes |
| **Example** |  `val x = 5` | `var y = 5` |
| **Best Use Cases** | Cnstants, values that won't change after initialization | Values that need to be updated over time |

#Summary
 `val` and `var` are two ways to declare variables.
 - **val** is used to decalre  a `read-only` or `immutable` variable.
 - **var** is used to declare a `mutable` variable.
