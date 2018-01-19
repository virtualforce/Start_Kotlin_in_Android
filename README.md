# Start Kotlin in Android
Here is the short guide introducing important elements of Kotlin with the provided examples to understand quickly how to start Kotlin in android development

## Prerequisites
Its recommended to install & configure Kotlin in Android Studio

## Getting Started
Let's start with an introduction of Kotlin

### Introduction
Kotlin is a JVM, or a Java Virtual Machine language. It can be run under any JVM. This means it can run on a server, or on Android. Kotlin can be used with Java or any other JVM based language. In fact, you don't have to completely rewrite your Android app to add new features, You can just add new Kotlin code and it will be compatible with your existing code base.
Just as **iOS** developers can turn to Swift if they want a modern language that's more approachable than Objective-C.

**Android** developers have Kotlin—an easy-to-use language that's highly compatible with Java. Along with improved syntax, Kotlin boasts null pointer safety with nullable variables, and lambda functions that allow you to develop your apps quickly and concisely.

This guide will cover the following elements:
1.	Syntax
2.	Variables
3.  Nullable Variables
4.	Functions
5.	Data Classes
6.	Companion Object
7.	Default Arguments
8.	Extension Functions
9.	Extension Properties

### 1. Syntax
- Syntax similar to Java and Swift
- Function definition: `fun <name> : <return value>`
- Control Statements similar to Java (except for when)
- Comments are same to Java
- Semicolons are optional

### 2. Variables
Kotlin is also strongly typed which means that you need to declare a variable to be a specific type. And it cannot change. There are two variable types:
- Val (cannot change)
```
  val name : String = "Hello"
```
- Var (changeable)
```
  var name : String = "Hello"
  name = "Hi"
```
**as** used for typecasting
```
 val toolbar = findViewById(R.id.toolbar) as Toolbar
```
### 3. Nullable Variables
One of the unique features of Kotlin is nullable types. In Android and Java, the null pointer exception is one of the biggest headaches we deal with. Kotlin can tell the difference between a variable that can be null and one that can't. To declare a variable is nullable, you need to add a question mark after the type. Note that only var types can be nullable, like:
```
var name : String? = null
```
and we can safely use while assigning it to new variable by adding question mark ahead of variable name,
```
val length = name?.length
```
here the Elvis operator is similar to Java's, but will take the value or the value on the other side of the Elvis operator, it means if name is null then use -1:
```
val length = name?.length ?: -1
```
If you are sure your variable can't be null, you can use two exclamation points if the variable's null, then a null pointer exception will occur, like:
```
val length = name!!.length
```
### 4. Functions
To create a function in Kotlin, start with the keyword **fun**. Add a name to the function and put parameters inside of parentheses. The parameters start with a name, then a colon, and then a type. You can also use default values for parameters. The function ends with a return type, if there is no return type, you can use a special class unit which is similar to Java's void, but is an actual class, or not specify a return type, like:
```
fun strLength(name: String?) : Int{
return name?.length ?: -1
}
```
if you want to override some funtion then you just need to append keyword **override** before fun, like:
```
override fun strLength(name: String?) : Int{
...
}
```
### 5. Data Classes
If you find yourself writing these boiler-plate methods all the time, data classes will save you time. Kotlin automatically creates getters, setters, equals, and hashCode methods for you. You'll just refer to the field, and Kotlin will use the getter/setter for that field, For example if you want to create data class of Customer with his name & age then you just need to write one line of code:
```
data class Customer(val name: String, val age: Int)
```
and to implement interface such as **Serializable** to pass it to another activity, we do this change:
```
data class Customer(val name: String, val age: Int) : Serializable
```

### 6. Companion Object
Companion object is Kotlin's way of creating constants and statics, let's create a companion object. And we're going to put our constant in here named photo and it's just going to have the name photo there:
```
companion object {
val PHOTO = "photo"
}
```
### 7. Default Arguments
Function parameters can have default values, which are used when a corresponding argument is omitted. This allows for a reduced number of overloads compared to other languages:
```
fun sendMoney(amount : Int, currency : String = "PKR") {
...
}
```
and we can call this function with:
```
sendMoney(10)
```
### 8. Extension functions
Extension functions are functions that, as the name implies, help us to extend the functionality of classes without having to touch their code. Now let’s see how these functions are defined, If you use Picasso library, for example, you need to load the image using the typical builder like this:
```
Picasso.with(imageView.context).load(url).into(imageView)
```
How would you like to be able to tell ImageView to upload a url by itself?
```
fun ImageView.loadUrl(url: String) {
    Picasso.with(context).load(url).into(this)
}
```
and now, call it directly from ImageView:
```
imageView.loadUrl(url)
```
### 9. Extension Properties
If there’s one or more properties you feel are missing from a class, then you can add them by creating an extension property for that class. For example, if you regularly find yourself writing the following bit of boilerplate:
```
PreferenceManager.getDefaultSharedPreferences(this)
```
then you can define it as property of Context like this:
```
val Context.preferences: SharedPreferences
       get() = PreferenceManager
       .getDefaultSharedPreferences(this)
```
now you can then use preferences as though it’s a property of Context:
```
context.preferences.contains("...")
```






