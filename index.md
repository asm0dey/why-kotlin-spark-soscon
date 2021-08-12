---
marp: true
theme: gaia
size: 4K
class: default
paginate: true
footer: '![](images/twitter_24.png) [asm0di0](https://twitter.com/asm0di0)'
backgroundImage: "linear-gradient(to bottom, #000 0%, #1a2028 50%, #293845 100%)"
color: white
title: Why Did We Create New API for Apache Spark
---
<!--
_class: lead
_paginate: false
_footer: ""
-->

<style>
footer {
    display: table
}
.hljs-variable { color: lightblue }
.hljs-string { color: lightgreen }
.hljs-params { color: lightpink }
</style>

![bg fit](images/1.png)

---

<!-- _class: lead -->
# Pasha Finkelshteyn

![bg brightness:40%](images/asm0dey.jpg)

Developer :avocado: for Big Data @ JetBrains

@asm0di0

---

# How did I fall in love with Big Data?

![bg right:35%](https://source.unsplash.com/iwFWEYMSVoI)

- 7 years ago Hadoop looked like a magic to Java enterprise developer
- Started to look for data-related projects
- Started to read about DBs
- Moved from Team Lead to Data Engineer

---

# Data engineers

Those who build your data pipelines
And your storage

---

# What did I have

- Java
- Kotlin
- Scala
- Groovy
- bash, XML, YAML :smile:

Sparse experience with other languages

---

# What did I have

- Core Java
- GC
- Lots of debug experience
- Distributed systems
- Architecture

---
<!-- _class: lead -->
# <!-- fit --> First thing Data Engineer learns?

---

![bg fit](images/spark.png)

---
<style scoped>
p > img {
    display: block;
    margin: auto;
}
</style>

# Example

![width:980](images/spark_scala.svg)

---
<style scoped>
p > img {
    display: block;
    margin: auto;
}
</style>

# Example

![width:980](images/spark_scala_2.svg)

---
<style scoped>
p > img {
    display: block;
    margin: auto;
}
</style>

# Example

![width:980](images/spark_scala_3.svg)

---
<style scoped>
p > img {
    display: block;
    margin: auto;
}
</style>

# Example

![width:980](images/spark_scala_4.svg)

---
<style scoped>
p > img {
    display: block;
    margin: auto;
}
</style>

# Example

![width:980](images/spark_scala_5.svg)

---

# Supported languages

![bg height:250](images/python.png) ![bg height:250](images/scala.png) ![bg height:250](images/java.svg) ![bg height:250](images/r.png)

---
<!-- _class: lead -->
# ![height:300](https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg)

### The most popular language in data engineering

---

![bg fit](images/spark1.png)

---

![bg fit](images/spark2.png)

---

![bg fit](images/spark3.png)

---

# Python

* `F` is made to distinct Spark built-ins from self-made.
  Who have ever created their own function over column?
* API is untyped
* Everything is string-based
* `UDF`s are SLOW
* Custom type support is complex

---

![bg fit](images/py4j.png)

---

<!-- _class: lead -->

![bg fit](images/scala.png)

---

# The best* official API

- Typed and untyped APIs
- Awesome smart encoders
- Spark is written in Scala:
    - Best interop possible
- Huge ecosystem

<small>* by my own rating among official APIs</small>

---

# The hard parts

![width:1140](images/types.png)

---

# The hard parts

![width:1140](images/zulimba.png)

---

# The hard parts

- Hard to learn for people without JVM knowledge
- Hard to read code somebody else wrote
- Easy to abuse language features
    - operator overloading
    - implicit
    - traits

---
<!-- _class: lead -->
# Scala's type system is awesome and powerful!

---

<!-- _class: lead -->
# Scala's type system is awesome and powerful!

Yes, but even Spark doesn't utilize it's full power

---

<!-- _class: lead -->
# Scala's type system is awesome and powerful!

Yes, but even Spark doesn't utilize it's full power

For the greater good

---

# Objects in Spark

![width:1200](images/objects1.png)

---

# Everything is expression

- `NewInstance`
- `ObjectType`
- `If`
- `IsNull`
- `Literal`

**Type safety is not silver bullet**

---

![bg fit](images/java.svg)

---

<!-- _class: lead -->

# Java is verbose

![bg right:60%](images/java.png)

---

<!-- # Java is verbose -->

![bg](images/encoders.png)

---
<!-- _class: lead -->
# <!-- fit --> Java is verbose

---

<!-- _class: lead -->
![bg fit](images/r.svg)


---

# R is hard
![bg fit](images/rdf1.png)

---

# R is hard
![bg fit](images/rdf2.png)

---

# R is hard
![bg fit](images/rdf3.png)


---

# Thoughts on R

- There are ideas on deprecating SparkR
- There always will be performance gap between native (JVM) and other languages

---

![bg height:650](images/kotlin.png)

---

# Null-aware type system
![](images/types-hier.png)

---

# Extension methods 

```kotlin
fun Iterable<Int>.sum() = reduce { a, b -> a + b }
```

---

# Extension methods 

```kotlin
fun Iterable<Int>.sum() = reduce { a, b -> a + b }
```

This :arrow_up: already exists in stdlib

---

# Join them together

Scala:

```scala
payment.join(customer, Seq("customerId"), "left_outer")
```

A bit later:

```scala
.map { _._2.id }
```

---

<!-- _class: lead -->

# <!-- fit --> `NullPointerException`:heart:

Because Java has unique exception for everything.

---

# We can do better

Kotlin:

```kotlin
payment.leftJoin(customer, col("customerId"))
```

A bit later

```kotlin
.map { it.second.id }
```
This :arrow_up: won't compile!

---

# We can do better

Kotlin:

```kotlin
payment.leftJoin(customer, col("customerId"))
```

A bit later

```kotlin
.map { it.second?.id }
```
This :arrow_up: will!

---

# DSL-building capabilities

![bg fit](images/dsl1.png)

---

# DSL-building capabilities

![bg fit](images/dsl6.png)

---

# Correct caching

![bg fit](images/cache2.png)

---

# `withSpark`

![bg fit](images/withspark1.png)

---

# `withSpark` signature

![bg fit](images/withspark.png)

---

# `withSpark` signature

![bg fit](images/withspark_sign2.png)

---

# Kotlin for Spark benefits

- Easy to read
- No encoders
- Null-safety
- Extension methods and DSL helpers
- Scala-like API
- Option to opt-out from any "non-native" experience
- Strong typing

---

# Things to improve

- ML support
- Better syntax for `UDF`s
- More audience
- More extensions
- Scala 3 (?)

---
<!-- 
_class: lead
_footer: "" 
_paginate: false
-->
# <!-- fit --> [github.com/JetBrains/kotlin-spark-api](github.com/JetBrains/kotlin-spark-api)

# Thank you! ![height:45](images/kotlin.png)

Pasha Finkelshteyn, JetBrains

![](images/twitter_24.png) [asm0di0](https://twitter.com/asm0di0)