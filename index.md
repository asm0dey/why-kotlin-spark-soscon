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

# Why Did We Create Kotlin API for Apache Spark

Pasha Finkelshteyn, JetBrains

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
<!-- _class: lead -->
# <!-- fit --> First thing Data Engineer learns?

---

![bg fit](images/spark.png)

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

# Supported languages

![bg height:250](https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg) ![bg height:250](images/scala.svg) ![bg height:250](images/java.svg) ![bg height:250](images/r.svg)

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

![bg fit](images/spark4.png)

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
<style scoped>
p > img {
    display: block;
    margin: auto;
}
</style>
# Python

![width:980](images/pydq.png)

---

<!-- _class: lead -->

# <!-- fit --> Scala

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

![width:1140](images/implicit.png)

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


