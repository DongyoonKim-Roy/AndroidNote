# Intent
## Definition :
  In Android, intents are a messaging mechanism used to communicate betweeen different components (such as activities, services, broadcas receivers) within an app, or even between different apps.
There are **Two types of intents** : **Explicit Intent** and **Implicit Intent**.

# Explicit Intent
![explicit](https://github.com/user-attachments/assets/e8e03da9-14bb-455c-9815-ee89e1d31307)
## Definition : 
  An **Explicit Intent** is used when you know the exact class (compontnt) you want to start. 
  For example, 
  1. Navigating from one activity to another within the same app.
  2. Starting a specific service or component where you know the exact destination.

# Code
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
