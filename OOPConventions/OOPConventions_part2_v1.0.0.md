# COMPANION OBJECT

- It should be placed at the beginning of its wrapper class.
- Name of constant is upper case and  specified with keywords **const val**.

**GOOD**

~~~kotlin
class MyFragment: Fragment() {
    companion object {
        const val TYPE_VIEW_HEADER: Int = 0
        const val TYPE_VIEW_FOOTER: Int = 1
    }
}
~~~

**BAD**

~~~kotlin
class MyFragment: Fragment() {
    companion object {
        val TypeViewHeader: Int = 0
        val TypeViewFooter: Int = 1
    }
}
~~~

- When you want to use components in Companion object, you should call directly.

**GOOD**

~~~kotlin
class MyClass {
   companion object {
       const val NUMBER: Int = 10
   }
}

val x: Int = MyClass.NUMBER
~~~

**BAD**

~~~kotlin
class MyClass {
   companion object {
       const val NUMBER: Int = 10
   }
}

val x: Int = MyClass.Companion.NUMBER
~~~

# EXTENSION FUNCTION

- Extension function is used when actually needed.
- Do not define extension function of a class in this class.

**GOOD**

~~~kotlin
class Person(val name: String) {
   // ...
}

fun Person.setName(name: String) {
   // ...
}
~~~

**BAD**

~~~kotlin
class Person(val name: String) {
   fun Person.setName(name: String) {
       // ...
   }
}
~~~

- Extension property should not use **this** to access to properties of the object applied.

**GOOD**

~~~kotlin
val <T> List<T>.lastIndex: Int
   get() = size - 1
~~~

**BAD**

~~~kotlin
val <T> List<T>.lastIndex: Int
   get() = this.size - 1
~~~

- When adding extensions to external classes, create a extension package and make separate files for each type:
 + StringExtensions.kt
 + BitmapExtensions.kt
 + ...

