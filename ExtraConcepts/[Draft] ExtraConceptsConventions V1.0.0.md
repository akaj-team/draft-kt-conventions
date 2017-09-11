# ENUM CLASS

Name of values in enum class same with name is uppercase.

~~~kotlin
enum class Day {
	MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
~~~

# EXCEPTIONS

**Kotlin** not auto suggest exceptions so when you feel suspect a exception can happen in your code, you must block it to try-catch expression.
In catch block you must define type of exception.

**Recommended**

~~~kotlin
try {
	…
} catch (et1 : ExceptionType1) {
	…
} catch (et2 : ExceptionType2) {
	…
}
~~~

**Not Recommended**

~~~kotlin
try {
	…
} catch (e : Exception) {
	…
}
~~~