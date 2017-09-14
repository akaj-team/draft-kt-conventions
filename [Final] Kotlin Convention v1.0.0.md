# Android Kotlin Conventions

## Info

> `GOOD` --> **Recommended**
>
> `BAD` --> **Not recommended**


## Structure
### •	Kotlin structure

~~~kotlin
vn.asiantech.project
	- api
	- models
	- managers
	- utils
	- fragments
	- service
	- interfaces
	- ui
 		 + screen_name_1
 		 + screen_name_2
	- views
~~~
### •	Resource structure
|  Name | Path  | Description |
| ------------- | ------------- | ------------- |
| XML Layouts | `res/layout/`  | This is where we put our XML layout files.
| XML Menus | `res/menu/` | This is where we put our AppBar menu actions.
| Drawables | `res/drawable` | This is where we put images and XML drawables.
| Colors | `res/values/colors.xml` | This is where we put [color definitions](https://developer.android.com/guide/topics/resources/more-resources.html).
| Dimensions | `res/values/dimens.xml` | This is where we put [dimension values](https://developer.android.com/guide/topics/resources/more-resources.html).
| String | `res/values/strings.xml` | This is where we put strings.
| Styles |` res/values/styles.xml`| This is where we put style values.
### Class
* First letter of classes is [UpperCase]().
* Name of class only accept in range **[A-Z], [a-z]** and follow **Camel Case**.
* Classes name must be **noun**.
* For classes that extend an Android component, the name of the class should end with the name of the component; for example: SignInActivity, SignInFragment, ImageUploaderService, ChangePasswordDialog.
* Open brace ‘ { ‘ appears at the end of the same line as the declaration statement.
* Closing brace ‘ } ‘ starts a line by itself indented to match its corresponding opening statement, except when it is a null statement the ‘ } ‘ should appear immediately after the ‘ { ‘
* Write KotlinDoc for each class, Kotlin doc must define what are classes working for.

**See Example**

~~~kotlin
/**
* Copyright © AsianTech Co., Ltd
* Created by toannt on 06/09/2017.
* SomeClass show information of user
*/
class SomeClass {
...
}
~~~
* Class member ordering
	There is no single correct solution for this but using a **logical** and **consistent** order will improve code learnability and readability. It is recommendable to use the following order:
	* Constants
	* Fields
	* Constructors
	* Override methods and callbacks
	* Public methods
	* Internal methods
	* Private methods
	* Inner classes and interfaces

`( TODO: inner class can be change position and some positions others)`

**Example**:

~~~kotlin
 class MainActivity : Activity() {

   var mTitle : String
   var mTextViewTitle : TextView

   override fun onCreate() {
        // Handle somthing
   }

   internal fun methodName () : Int {
        // Handle somthing
   }

   private fun setUpView() {
        // Handle somthing
   }
}
~~~

If your class is extending an **Android components** such as an Activity or a Fragment, it is a good practice to order the override methods so that they **match the component’s lifecycle**. For example, if you have an Activity that implements **onCreate()**, **onDestroy()**, **onPause()** and **onResume()**, then the correct order is:

~~~kotlin
 class MainActivity : Activity() {
  // Order matches Activity lifecycle
  override fun onCreate() {}

  override fun onResume() {}

  override fun onPause() {}

  override fun onDestroy() {}
}
~~~
### Method
* Short method content:
Method content should be short and focus on the feature of method. Avoid repeating code.
* Code line not over 80 characters. Except for inputting text or URL.
* Method name must start with verb is first letter.
* First letter of method name is **LOWERCASE**.
* @SuppressWarnings: The ***@SupperssWarnings*** annotation should only be used under circumstances where it is impossible to eliminate a warning. If a warning passes this ”impossible to eliminate” test, the ***@SuppressWarnings*** annotation must be used, so as to ensure that all warnings reflect actual problems in the code.

**Example**

* Write document for methods if it’s necessary.

~~~kotlin
/**
* Format date
*
* @param dateFormat Date need format
* @return the date formatted
* @throw ParseException exception
*/
fun formatDate(dateFormat: String): String {
// Handle somthing
}
~~~

* Limit method block line less than **300** lines, limit method arguments less than **5**. Separate code if function has long line method.
* If statement convention.

**GOOD**

~~~kotlin
 if (…) {
  doSomething()
 }
~~~

**BAD**

~~~kotlin
if (…)
doSomething()
~~~
* Use `// TODO` for dummy data or need to change later.

~~~kotlin
// TODO Remove after api finish
~~~
* Catch exception.

**GOOD**

~~~kotlin
try {
    // Handle somthing
} catch (et1 : ExceptionType1) {
    // Handle somthing
} catch (et2 : ExceptionType2) {
    // Handle somthing
}
~~~
**BAD**

~~~kotlin
try {
    // Handle somthing
} catch (e : Exception) {
    // Handle somthing
}
~~~
### Variable:

`TODO: Update more in future`

* All  letters of constant name is UPPERCASE

~~~kotlin
companion object {
    const val GOOGLE_HOME_URL = "http://www.google.com"
}
~~~

### XML Conventions
* `View ID` is followed by camel-case, example:

~~~kotlin
btnLogin, tvCaption
~~~
* Prefix for `id` in XML


| Name | Prefix  | Name | Prefix
| ------------- | ------------- | ------------- | ------------- |
| `Button`  | `btn`  | `Datepicker`  | `datePicker` |
| `EditText`  | `edt`  | `Timepicker`  | `timePicker` |
| `TextView`  | `tv`  | `Videoview`  | `videoView` |
| `Checkbox`  | `chk`  | `Seekbar`  | `seekBar` |
| `RadioButton`  | `rb`  | `RatingBar`  | `ratingBar` |
| `ToggleButton`  | `tb`  | `Processbar`  | `processBar` |
| `Spinner`  | `spn`  | `ImageView`  | `img` |
| `Menu`  | `menu`  | `ImageButton`  | `imgBtn` |
| `ListView`  | `lv`  | `RecyclerView`  | `recycleView` |
| `GalleryView`  | `gv`  | `CardView`  | `cardView` |
| `LinearLayout`  | `ll`  | `ScrollView`  | `scrollView` |
| `RelativeLayout`  | `rl`  | `ToolBar`  | `toolbar` |
| `Calendar`  | `calendar`  |  | |


* XML File Name:

	* Item for list view: `item_list _*`
	* Item for grid view: `item_grid _*`
	* Custom for view: `custom_*`
	* Custom for dialog: `dialog_*`

**Example:**

~~~xml
@+id/tvSubjectQuestions
@+id/ivTakeCamera
~~~

* Image name
	* Icon: `ic_*`
	* Background: `bg_*`
	* Image: `img_*`
* Other naming
	* Model (example: Student, Teacher)
	* Activity: `*Activity` ( example: UserActivity)
	* Fragment: `*Fragment` (example: HomeFragment)
	* Apdater: `*Adapter` (example: PageAdapter)
* Do not make a deep hierarchy of `ViewGroups`. [here](https://github.com/futurice/android-best-practices#deephierarchy)
* Also keep `dimens.xml` DRY, define generic constants. [here](https://github.com/futurice/android-best-practices#dimensxml)
* Use multiple style files to avoid a single huge one. [here](https://github.com/futurice/android-best-practices#splitstyles)
* When an XML element doesn’t have any contents, you **must** use self closing tags.

**GOOD**

~~~xml
<TextView
	android: id="@+id/text_view_profile"
	android: layout_width="wrap_content"
	android: layout_height="wrap_content" />
~~~
**BAD**

~~~xml
<!-- Don\'t do this! -->
<TextView
	android: id="@+id/text_view_profile"
	android: layout_width="wrap_content"
	android: layout_height="wrap_content" >
</TextView>
~~~

## Basic Kotlin

### Variables

* Write in **lowerCamelCase**

* Single character value must be avoided, except for temporary looping variables.

**GOOD**

~~~kotlin
var studentName: String
~~~

**BAD**

~~~kotlin
var StudentName: String
~~~

### Type Inference

* Type inference should be preferred where possible to explicitly decleard types

**GOOD**

~~~kotlin
val student = Student()
val age = 21
~~~

**BAD**

~~~kotlin
val student: Student = Student()
val age: Int = 21
~~~

### Strings

* Always prefer string interpolation if possible.

**GOOD**

~~~kotlin
val name = "${user.firstName} ${user.lastName}"
~~~

**BAD**

~~~kotlin
val name = user.firstName + " " + user.lastName
~~~

### If Expression

**GOOD**

~~~kotlin
if (someTest) {
// Handle somthing
} else {
// Handle somthing
}
~~~

**BAD**

~~~kotlin
if (someTest) {
// Handle somthing
}
else {
// Handle somthing
}
~~~

### When Expression

* Unlike `switch` statements in Java, `when` statements do not fall through. Separate cases using commas if they should be handled the same way. Always include the else case.

**GOOD**

~~~kotlin
when (Input) {
    1, 2 -> doSomethingForCaseOneOrTwo()
    3 -> doSomethingForCaseThree()
    else -> print("No case satisfied")
}
~~~

**BAD**

~~~kotlin
when (Input) {
    1 -> doSomeThingForCaseOne()
    2 -> doSomeThingForCaseOneOrTwo()
    3 -> doSomeThingForCaseThree()
}
~~~

### Smart Cast

**GOOD**

~~~kotlin
dog as? Animal ?: throw IllegalArgumentException("not Animal!")
dog.foo()
~~~

**BAD**

~~~kotlin
if (dog !is Animal) {
    throw IllegalArgumentException("not Animal!")
}
dog.foo()
~~~

### Collections

* Should be used `MutableList` if that `List` change data in future
* If you create the list to read only, you can use `List` instead of using `MutableList`

**GOOD**

~~~kotlin
val students: MutableList<Int> = ArrayList()
~~~

**BAD**

~~~kotlin
val students :List<Int> = ArrayList()
~~~

### Equality

* Should be used equal instead of "==" operator

**GOOD**

~~~kotlin
a.equal(b)
!a.equal(b)
~~~

**BAD**

~~~kotlin
a == b
a != b
~~~

### This Expression

* Don't use `this@label` if compiler understood that `this`

**GOOD**

~~~kotlin
data class Test(var name: String) {

    fun showName(name: String) {
        this.name = name
    }
}
~~~

**BAD**

~~~kotlin
data class Test(var name: String) {

    fun showName(name: String) {
        this@Test.name = name
    }
}
~~~

## OOP Kotlin

### Visibility Modifiers

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

### Class

- **Constructor**: Initialize class properties as **primary constructor** parameters instead of in an **init** block.

**GOOD**

~~~kotlin
class Person (val firstName: String, val lastName) {
    // handle something
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

  	// handle something
}
~~~

### Function

- If a function returns **Unit**, the return type should be omitted.

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

- If the function has an empty body, use the **Unit** type instead of empty bracket body.

**GOOD**

~~~kotlin
fun doNothing() = Unit
~~~

**BAD**

~~~kotlin
fun doNothing() {
	// No opp
}
~~~

### Data class

Only using **data** keyword when class need equals(), hashCode(), toString(), copy(), componentN() function. Example: Models class.

### Generics

When define an object of a **generic** class we don't need define type of that object.

~~~kotlin
class Food<T>(kind: T) {
	var value = kind
}
~~~

**GOOD**

~~~kotlin
val fish = Food("Fish")
~~~

**BAD**

~~~kotlin
val fish: Food<String> = Food<String>("Fish")
~~~

### Companion Object

- It should be placed at the beginning of its wrapper class.
- Name of constants is upper case and  specified with keywords **const val**.

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

- When you want to use components in companion object, you should call directly.

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

### Extension funtion

- Extension function is used when actually needed.
- Do not define extension function of a class in this class.

**GOOD**

~~~kotlin
class Person(val name: String) {
   // handle somethings
}

fun Person.setName(name: String) {
   // handle somethings
}
~~~

**BAD**

~~~kotlin
class Person(val name: String) {
   // handle somethings
   
   fun Person.setName(name: String) {
       // handle somethings
   }
}
~~~

- Extension property should not use **this** keyword to access to properties of the object applied.

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

### Destructuring Declarations

-  Paramaters should directly destructer without componentN()

**GOOD**

~~~kotlin
data class Person(var name: String, var age: Int) {
    // handle somethings
}

val person = Person("Nguyen Van A", 22)
val (name, age) = person
println("Name:$name,Age:$age")
~~~

**BAD**

~~~kotlin
data class Person(var name: String, var age: Int) {
    // handle somethings
}

val person = Person("Nguyen Van A", 22)
val name = person.component1()
val age = person.component2()
println("Name:$name,Age:$age")
~~~


### High-Order Functon

- Parameters in high-order function are placed in order: normal paramaters, functions.

**GOOD**

~~~kotlin
fun <T> lock( lock: Lock, body: () -> T) {
   // handle somethings
}
~~~

**BAD**

~~~kotlin
fun <T> lock(body: () -> T, lock: Lock) {
   // handle somethings
}

~~~

### Lambda

-  Should ignore **()**, **->**, **name parameter** and use **it** keyword to declare the parameter explicitly if the function has only  one parameter as lambda block.

**GOOD**

~~~kotlin
fun onClick(position: (Int) -> Unit) {
   // handle somethings
}

onClick { println(it) }
~~~

**BAD**

~~~kotlin
fun onClick(position: (Int) -> Unit) {
   // handle somethings
}

onClick({ position -> println(position) })
~~~

- Should place lambda block out of the round bracket of the function if a function has more than one parameter.

**GOOD**

~~~kotlin
fun onClick(x: String, data: (Int, String) -> Unit) {
   // handle somethings
}
onClick("abc") { position, content ->
   println("Position: $position, Content: $content")
}
~~~

**BAD**

~~~kotlin
fun onClick(x: String, data: (Int, String) -> Unit) {
   // handle somethings
}

onClick("abc", { position, content ->
   println("Position: $position, Content: $content")
})
~~~

### Inline keyword

- An inline function is used for small functions(1 -> 5 lines of code), not used for big functions.
- The inline modifier can be used on accessors of properties when we do not want to create a backing field.

**GOOD**

~~~kotlin
inline var bar: Bar
    get() = // handle somethings
    set(v) { // handle somethings }
~~~

**BAD**

~~~kotlin
var bar: Bar
    get() = // handle somethings
    set(v) { // handle somethings }
~~~


## Environments
* Android Studio. [download]( https://developer.android.com/studio/index.html)
* Setup Kotlin plugin.

## Framework Conventions ( TODO: Will update later)
## Security Conventions
* Remember cancel Thread, Asyntask, …if go out other screen or turn back home screen.
* Remember enable minifyEnabled function in build.gradle while on release mode and config proguard carefully.

~~~Groovy
     buildTypes {
         release {
             debuggable false
             minifyEnabled true
             proguardFiles getDefaultProguardFile('proguard-android.txt' ), 'proguard-rules.pro'
             applicationVariants. all { variant ->
             appendVersionNameVersionCode(variant)
             }
         }
     }
~~~

* If you guys create keystore by yourself, let talk to PM or TL about that, and having backup that keystore carefully and remember information of keystore (keyAlias, keyPassword).
* Don’t push keystore file and information of keystore to GitHub, keep it in local as in local.properties file.
* More practice:
	1. [Proguard configure](https://github.com/futurice/android-best-practices#proguard-configuration)
	2. [Gradle configure](https://github.com/futurice/android-best-practices#gradle-configuration)

	**local.properties file**

~~~
 sdk. dir=/Users/Administrator/Library/Android/sdk
 keyAlias=sampletext1
 keyPassword= sampletext2
~~~
* Verify input validation carefully.
* Verify Runtime Permission function available in Android 6.0 and above carefully. [More details](https://developer.android.com/training/permissions/requesting.html)
* Avoid leak memory. [More details](http://blog.nimbledroid.com/2016/09/06/stop-memory-leaks.html)
* Avoid out of memory. [More details](http://marcusjenkins.com/avoid-out-of-memory-problems-in-android/)
* Avoid run time exception

## Code management practices and Dependency management practices
* Introduce [Gradle Tool](https://github.com/futurice/android-best-practices#build-system)

## References
* Android practices [Github](https://github.com/futurice/android-best-practices)
* [KotlinLang](https://kotlinlang.org/docs/reference/)
* Android Developer [Page](https://developer.android.com/index.html)
* Kotlin Code Coventions [Page](https://kotlinlang.org/docs/reference/coding-conventions.html)

## Code review Checklist
* Pass Circle CI or Travis CI with checktyle findbug lint tools: 70% follow convention.
* Pass Reviewer: 30% follow convention.
* Github

## More References
* [Android Boilerplate](https://github.com/ribot/android-boilerplate)
* [Android folder structure](https://guides.codepath.com/android/Organizing-your-Source-Files#android-folder-structure)
