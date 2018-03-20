# Super Basic Quick Start

We'll be cloning and building a very basic Android project, which shares
just a little bit of standard Java code.

The iOS Xcode project that consumes the generated code is ready to go,
so all we'll be doing is making sure the necessary tools are installed and running
everything. Not counting download time, assuming no install issues, this whole
thing should take 5-10 minutes.

## Prerequisites

+ A macos computer. You can run J2objc on another machine, but you won't be able to do much with it.
+ [Android Studio](https://developer.android.com/studio/index.html)
+ Xcode
+ [Cocoapods](https://cocoapods.org/)

## Clone Repo

Clone the [BasicAndroidSample](https://github.com/j2objcgradle/BasicAndroidSample)

```bash
git clone https://github.com/j2objcgradle/BasicAndroidSample.git
cd BasicAndroidSample
```

## Build and run iOS

We can walk through more details later, but to see the plugin function, we'll
run J2objc on the shared Java code, then open and run the project in Xcode.

```bash
./gradlew j2objcBuild
```

Assuming this the first run, the plugin will download a J2objc runtime. It will take
some time. You should see download status updates output to terminal.

If everything comes out OK, the next step is to run Cocoapods. The gradle plugin
generates a definition file which points at the generated code. Running Cocoapods
will wire the generated code to the Xcode project.

```bash
cd ios
pod install
```

Navigate in Finder to the project directory, open the 'ios' folder, and double-click
'ios.xcworkspace'.

Select a simulator to run, and click 'Run'.

If everything is set up correctly, you should see the app launch.

## Video Tutorial

Watch the setup process here

[![Quick Start Tutorial Video](https://img.youtube.com/vi/ecX74fpHtOo/0.jpg)](https://www.youtube.com/watch?v=ecX74fpHtOo)

## Project Detail

### Gradle Config

The plugin and available libraries are currently kept in a bintray maven repository. The repo is at 'https://dl.bintray.com/doppllib/j2objc'.
In general you'll want to add the repo to both the buildscript and project repository collections. Also add 'org.j2objcgradle:gradle:0.12.1' to the
buildscript dependencies.

```gradle
buildscript {
    ext.kotlin_version = '1.1.51'
    repositories {
        google()
        jcenter()
        maven { url 'https://dl.bintray.com/doppllib/j2objc' }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.0.1'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
        classpath "org.j2objcgradle:gradle:0.12.1"
    }
}

allprojects {
    repositories {
        google()
        jcenter()
        maven { url 'https://dl.bintray.com/doppllib/j2objc' }
    }
}
```

The J2objc Gradle plugin can operate in two basic contexts: a separate Java module, and inside an Android project module.
Inside a Java module, generally all of the Java code is shared to Objective-C. In an Android module, the shared
code needs to be identified in the plugin config.
