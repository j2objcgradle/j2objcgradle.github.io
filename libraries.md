# Libraries

Here's a list of the libraries we're currently working with.

## Core J2objc

J2objc ships with a few libraries. Rather than using the compiled versions, we've created Gradle dependencies from
them so the Gradle plugin only needs the jre-emul libraries from J2objc's distribution.

### JUnit4

JUnit in J2objc is just the source jar translated, with Hamcrest.

+ JUnit [4.12](https://github.com/j2objcgradle/junit4/tree/j2objc-4.12)
+ JavaHamcrest [1.3](https://github.com/j2objcgradle/JavaHamcrest/tree/j2objc-1.3)

### Mockito

J2objc has a highly modified implementation of Mockito that works in Objective-C. Again, we've
packaged this up as a Gradle dependency rather than carry around J2objc's artifacts. However, 2 important notes.
Spy is not supported by J2objc's implementation. We have a very hacked support of spy available, but hopefully
somebody soon will create a real implementation. Also, J2objc's version is 1.9.5, which is fairly old
for Mockito. Version 2+ of Mockito itself is significantly different, so somebody would need to
put some serious effort into sort that out.

+ Mockito [1.9.5](https://github.com/j2objcgradle/mockito/tree/j2objc-1.9.5)

### jsr305 and javax.inject

The J2objc Gradle plugin just includes these two dependencies on all builds. We use them everywhere, and
they're relatively small, so we [just put them in there](https://github.com/j2objcgradle/gradle/blob/master/src/main/groovy/org/j2objcgradle/gradle/J2objcPlugin.groovy#L122).

```groovy
compileOnly 'com.google.code.findbugs:jsr305:3.0.2'
testImplementation 'com.google.code.findbugs:jsr305:3.0.2'
j2objcOnly 'com.google.code.findbugs:jsr305:3.0.2:sources'

compileOnly 'javax.inject:javax.inject:1'
testImplementation 'javax.inject:javax.inject:1'
j2objcOnly 'javax.inject:javax.inject:1:sources'
```

## Other Libs

### Gson

Gson is one of the first libraries pretty much everybody translates for J2objc.

+ Gson [2.6.2](https://github.com/j2objcgradle/gson/tree/j2objc-2.6.2), [2.8.2](https://github.com/j2objcgradle/gson/tree/j2objc-2.8.2)

## Doppl
