# asdf

**Why add these libraries if J2objc already has them?**

The Gradle plugin defines transitive dependency configs that make adding J2objc dependencies more homogenous and "Gradle-like".

```gradle
testImplementation "junit:junit:4.12"
testJ2objc "org.j2objcgradle.junit:junit:4.12.0"
```

Although the Gradle plugin now works with stock J2objc, it only uses the JRE runtime from the J2objc project itself, and other
libraries are included through Java source and Gradle config, and transformed to Objective-C with other dependencies. The plugin
itself can download and install a J2objc runtime, and we have a significantly smaller (325m) runtime download package available.
