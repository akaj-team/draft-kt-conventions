#BASIC KOTLIN CONVENTION

## Variables

* Write in **lowerCamelCase**

* Single character value must be avoided, except for temporary looping variables.

**GOOD**

~~~Kotlin
var nameStudent: String
~~~

**BAD**

~~~
var NameStudent: String
~~~

* All letters of constant name is `UPPERCASE`

**GOOD**

~~~
class MainFragment: Fragment() {
    companion object {
        const val TYPE_VIEW_HEADER = 0
        const val TYPE_VIEW_FOOTER = 1
    }
}
~~~

**BAD**

~~~
class MainFragment: Fragment() {
    companion object {
        val TypeViewHeader = 0
        val TypeViewFooter = 1
    }
}
~~~

## Type Inference

* Type inference should be preferred where possible to explicitly decleard types

**GOOD**

~~~
val something = YourType()
val age = 21
~~~

**BAD**

~~~
val something: YourType = YourType()
val age: Int = 21
~~~

## Constructor

**GOOD**

~~~
class User(
    public open var firstName: String,
    public open var lastName: String
) {}
~~~

**BAD**

~~~
class User(public open var firstName: String, public open var lastName: String){}
~~~

## Strings

* Always prefer string interpolation if possible.

**GOOD**

~~~
val name = "${user.firstName} ${user.lastName}"
~~~

**BAD**

~~~
val name = user.firstName + " " + user.lastName
~~~

## If Expression

**GOOD**

~~~
if(someTest) {
...
} else {
...
}
~~~

**BAD**

~~~
if (someTest) {
...
}
else {
...
}
~~~

## Loop

* You don't have to write for loop because there is `forEach` in collection package of Kotlin

**GOOD**

~~~
(0..9).forEach{
...
}

// or if you want to know index

(0..0).forEachIndexed{ index, value	->
...
}
~~~

**BAD**

~~~
for (i in 0..9){
...
}
~~~

## When Expression

* Unlike `switch` statements in Java, `when` statements do not fall through. Separate cases using commas if they should be handled the same way. Always include the else case.

**GOOD**

~~~
when (anInput) {
	1, 2 -> doSomethingForCaseOneOrTwo()
    3 -> doSomethingForCaseThree()
    else -> print("No case satisfied")
}
~~~

**BAD**

~~~
when (anInput) {
	1 -> doSomeThingForCaseOne()
    2 -> doSomeThingForCaseOneOrTwo()
    3 -> doSomeThingForCaseThree()
}
~~~

## Smart Cast

**GOOD**

~~~
dog as? Animal ?: throw IllegalArgumentException("not Animal!")
dog.foo()
~~~

**BAD**

~~~
if (dog !is Animal) {
    throw IllegalArgumentException("not Animal!")
}
dog.foo()
~~~
	
