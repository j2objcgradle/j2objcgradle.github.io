# Gradle for J2objc

This github org contains both a gradle plugin to support building J2objc and
several core libraries that can be included as dependencies.

+ [gradle](https://github.com/j2objcgradle/gradle) - The gradle plugin
+ [junit4](https://github.com/j2objcgradle/junit4) - Junit4
+ [mockito 1.9.5](https://github.com/j2objcgradle/mockito) - Mockito with some Objective-C specific additions (from the J2objc project)
+ [JavaHamcrest](https://github.com/j2objcgradle/JavaHamcrest) - JavaHamcrest provided to support junit4

## Gradle Plugin

The gradle plugin is a fork of [j2objc-contrib/j2objc-gradle](https://github.com/j2objc-contrib/j2objc-gradle). That
project is no longer maintained, and we may merge the two. However, they're pretty different in how they operate at this point.
Read more about the history at [gradlehistory](gradlehistory.html).

## Libraries

The libraries included in this org are going to be very core, Java-only libraries. Junit and mockito come straight out of the J2objc
project itself.

**Why add these libraries if J2objc already has them?**

The Gradle plugin defines transitive dependency configs that make adding J2objc dependencies more homogenous and "Gradle-like".

```gradle
testImplementation "junit:junit:4.12"
testJ2objc "org.j2objcgradle.junit:junit:4.12.0"
```

Although the Gradle plugin now works with stock J2objc, it only uses the JRE runtime from the J2objc project itself, and other
libraries are included through Java source and Gradle config, and transformed to Objective-C with other dependencies. The plugin
itself can download and install a J2objc runtime, and we have a significantly smaller (325m) runtime download package available.
