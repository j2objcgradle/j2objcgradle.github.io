# Gradle Plugin History

The gradle plugin started as a fork of https://github.com/j2objc-contrib/j2objc-gradle. That plugin
uses native compilation features of Gradle, which no longer function as of Gradle 2.8. Current
Android development requires far newer versions of Gradle to be productive.

Doing the native compilation and testing in the Gradle plugin also created a black box situation.
Compiling, linking, and testing Objective-C code inside of Gradle tasks creates a very non-standard
build situation. Finding support on StackOverflow is going to be very difficult for these issues.

The decision was made to reduce the responsibility of the plugin to managing dependencies and
generating Objective-C, and rely on Xcode or other command line build tools that are more
common for iOS development to actually build and link iOS code. This would increase the liklihood
of finding support online and using more common tools for those jobs (although obviously if individual
teams wanted to have a 100% Gradle build chain, they could investigate options on their own).

Another major issue was Xcode and nested source paths. Java imposes a folder based package organization system which,
while familiar to Java developers, is relatively uncommon in other development ecosystems. Out of the box, J2objc
outputs files in a similar fashion, but Xcode doesn't ingest that format well.

The forked Gradle plugin also resulted in a forked J2objc, which ultimately was packaged into a different
name called "Doppl". The original concept of "Doppl" includes architectural constructs from Android
that allow significantly more code sharing between platforms. Since our build system had both a forked
Gradle plugin and a forked J2objc, the whole thing was just called "Doppl".

After roughly a year of iterations, the only outstanding J2objc differences were minor, so over the early
months of 2018 those were resolved to return to a stock J2objc runtime. As of right now (3/20/2018) the
Gradle plugin and all of the libraries we support are compatible with current J2objc source. The current J2objc
release, 2.0.5, would not work, but that should be updated soon.

Since the Gradle plugin and many of the libraries are core "Java" without the Android extensions,
we've split off two different development paths and Github orgs. If it makes sense to the authors and users of the
original J2objc-Gradle plugin to merge this fork, then that might happen in the near future.

Although this plugin has drifted fairly significantly from the original version,
this project almost certainly wouldn't exist without the efforts of the original authors.

## j2objc-gradle

Gradle plugin for j2objc (Java to Objective-C transpiler)

https://github.com/j2objc-contrib/j2objc-gradle

Copyright (c) 2015-2016 the authors of j2objc-gradle

Main Contributors:
  Advay Mengle @advayDev1 <source@madvay.com>
  Bruno Bowden @brunobowden <github@brunobowden.com>
  Michael Gorski @confile <mail@michaelgorski.de>

Thanks:
  Peter Niederweiser @pniederw <peter@pniederw.com>
  Sterling Greene @big-guy <sterling.greene@gradleware.com>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this software except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

This serves as the NOTICE under Section 4 d of the License.
