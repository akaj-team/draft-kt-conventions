# Visibility Modifiers

- **Kotlin** have 4 **visibility modifiers: public, internal, protected, private.** But when we using we must define **visibility modifier** that have the smallest range of use.
- If **visibility modifiers** is **public**, omitted it:

**GOOD**

~~~kotlin
val name: String = "This is name"
~~~

**BAD**

~~~kotlin
public val name: String = "This is name"
~~~

# Class

- **Constructor**: Initialize class properties as primary constructor parameters instead of in an init block.

**GOOD**

~~~kotlin
class Person (val firstName: String, val lastName) {
    ...
}
~~~

**BAD**

~~~kotlin
class Person (firstName: String, lastName: String) {
  	val firstName: String
  	val lastName: String

  	init {
		this.firstName = firstName
		this.lastName = lastName
  	}

  	...
}
~~~

# Function
 
- If a function returns Unit, the return type should be omitted.

**GOOD**

~~~kotlin
fun showText (text: String) {
   	println(text)
}
~~~

**BAD**

~~~kotlin
fun showText (text: String): Unit {
    println(text)
}
~~~

- If the function only executes an expression, the expression should be placed on the declaration line.

**GOOD**

~~~kotlin
fun sum (a: Int, b: Int): Int = a + b
~~~

**BAD**

~~~kotlin
fun sum (a: Int, b: Int): Int {
 	return a + b
}
~~~

- If the function has an empty body, use the Unit type instead of empty bracket body.

**GOOD**

~~~kotlin
fun doNothing() = Unit
~~~

**BAD**

~~~kotlin
fun doNothing() {
	...
}
~~~ 

# Data class
Only using data keyword when class need equals(), hashCode(), toString(), copy(), componentN() function. Example: Models class.
 
# Generics
When define an object of a generic class we don't need define type of that object.

~~~kotlin
class Food<T>(kind: T) {
	var value = kind
}
~~~

**GOOD**

~~~kotlin
val food1 = Food("value")
~~~
**BAD**

~~~kotlin
val food1: Food<String> = Food<String>("value")
~~~ 
