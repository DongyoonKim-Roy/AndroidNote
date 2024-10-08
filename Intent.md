# Intent
  In Android, intents are a messaging mechanism used to communicate betweeen different components (such as activities, services, broadcas receivers) within an app, or even between different apps.
There are **Two types of intents** : **Explicit Intent** and **Implicit Intent**.

# Explicit Intent
![explicit](https://github.com/user-attachments/assets/e8e03da9-14bb-455c-9815-ee89e1d31307)

## Definition  
  An **Explicit Intent** is used when you know the exact class (compontnt) you want to start. 
  For example, 
  1. Navigating from one activity to another **within the same app**.
  2. Starting a specific service or component where you know the exact destination.

## Example
```
  val explicitButton = findViewById(R.id.explicitButton)
  explicitButton.setOnClickListner(){
    val intent = Intent(this, SecondActivity::class.java)
    startActivity(intent)
    finish()
  }
```
> [val VS var](https://github.com/DongyoonKim-Roy/AndroidNote/blob/main/val%20VS%20var.md), [SecondActivity::class.java](https://github.com/DongyoonKim-Roy/AndroidNote/blob/main/Activity%3A%3Aclass.java.md), [R.id](https://github.com/DongyoonKim-Roy/AndroidNote/blob/main/R.id.md)

# Implicit Intent
![implicit](https://github.com/user-attachments/assets/502c9203-ec91-486b-93d1-714a4dc5923c)

## Definition 
  An **Implicit Intent** does not specify the target component directly.
  Instead, it specifies the action that needs to be performed and allows the sysem to determine which component(s) can handle that action.
  For example,
  1. When you want to open a web page, send an email or share data **using another app**.
  2. when you need to request an action but **do not care which specific app or component handles it** (e,g., opening a file or starting a camera).

## Example
```
  val url - "https://google.com"
  val implicitButton = findViewById(R.id.implicitButton)
  implicitButton.setOnClickListner(){
    val intent = Intent(Intent.ACTION_VIEW, Uri.parse(url))
    startActivity(intent)
    finish()
  }
```

# Key Differences Between Explicit and Implicit Intent 
| **Aspect** | **Explicit** | **Implicit** |
| ----------      | -----------       |      ------------  |
| **Component Targeting** | Specify the exact target component by name. | Specify an action, and Android finds a suitable component. |
| **Use case** | Communication within the app (Between activities or servicies) | Delegating an action to another app or letting the system choose a component. |
|**Example Action** | Starting a specific activity `(SecondActivity)` | Opening a web page sending an email, or sharing data. |
| **Example Intent** | `Intent(this, SecondActivity::class.java)` | `Intent(Intent.ACTION_VIEW, Uri.parse("https://google.com"))` |
