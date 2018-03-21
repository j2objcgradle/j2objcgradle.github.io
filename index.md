# Gradle for J2objc

This project contains both a gradle plugin to support building [J2objc](https://developers.google.com/j2objc/) and
several core libraries that can be included as dependencies.

## Getting Started

To see how to run the Gradle plugin against a basic project, check out [Basic Quickstart](basicquickstart.html).

After the quickstart, see [more samples and tutorials](moresamples.html) for next steps.

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
