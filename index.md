# J2objc Packager for Gradle

This project contains both a gradle plugin to support translating Java to Objective-C with [J2objc](https://developers.google.com/j2objc/), with
dependency and packaging support for Xcode using Cocoapods.

## Getting Started

To see how to run the Gradle plugin against a basic project, check out [Basic Quickstart](basicquickstart.html).

After the quickstart, see more tutorials in the menu under "Basic Quickstart/Tutorials".

## Gradle Plugin / Doppl

The gradle plugin is a fork of 'j2objc-contrib/j2objc-gradle',
and was the Gradle plugin developed for the [Doppl Project](https://doppllib.github.io/). See [gradlehistory](gradlehistory.html)
for more background info and context.

## Libraries

The libraries included in this org are going to be very core, Java-only libraries. Junit and mockito come straight out of the J2objc
project itself.

+ [junit4](https://github.com/j2objcgradle/junit4) - Junit4
+ [mockito 1.9.5](https://github.com/j2objcgradle/mockito) - Mockito with some Objective-C specific additions (from the J2objc project)
+ [JavaHamcrest](https://github.com/j2objcgradle/JavaHamcrest) - JavaHamcrest provided to support junit4

See the [github page](https://github.com/j2objcgradle) for the current status and list. More experimental stuff will be at
[Doppl Github](https://github.com/doppllib/).

More info about [core J2objc libraries and the Gradle plugin](gradleandj2objc.html).
