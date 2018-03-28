# Android Stuff

> See other tutorials in menu under "Basic Quickstart / Tutorials"

So far we've been mostly talking about vanilla Java code translation. While
this can certainly be useful, the original purpose of Doppl and the origin of this
Gradle plugin is focused on sharing architecture.

Android and iOS are very, very similar platforms below the UI. This sounds like a
crazy statement, but it's true. They're both Unix-y systems, with threads, networking,
local files, SQLite, etc. Fault tolerant, testable, mobile *architecture* is not platform specific.
The Android community has tended to focus on MVP, MVVM, MVI, and the iOS community seems
to favor VIPER, but nothing about these architectures is specific to the platforms outside of
community preference.

The Doppl project includes several structures from Android AOSP that facilitate
sharing of both logic and architecture. This includes the SQLite stack, Shared Preference,
Android threading, local file access, and a few classes that aren't used on iOS but
help compatibility (Bundle, Parcelable, etc).

Adding this base of Android architecture also allows us to add a number of popular libraries
on top, including Android Architecture Components, Retrofit, RxJava/RxAndroid, etc.

You can find more Doppl samples in the [Doppl Project](https://doppllib.github.io/), but we'll add some Shared Preference
storage to the sample app to go over the basics.

## Configure Project

Add Doppl dependencies.

```groovy
j2objc "co.doppl.lib:androidbase:0.9.0.0"
```

You should only add the j2objc dependency because 'androidbase' includes classes already
defined in "Android". If you are building a separate Java module, add the implementation dependency as well.

In future releases we'll be splitting out the separate service dependencies, but for now,
all of the additional Android "stuff" is in one project: [core-doppl](https://github.com/doppllib/core-doppl).

After running './gradlew j2objcBuild' you'll need to run 'pod install' again because androidbase
defines a few C++ files that Xcode needs to know about.

## Init Doppl Runtime

Open AppDelegate.swift and add DopplRuntime.start()

```swift
import UIKit
import j2objclib

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        DopplRuntime.start()
        return true
    }
    ...
}
```

To use shared preferences we need to create a Context instance then pass it to the AppPrefs object.
In a full app you should only create 1 Context instance. Just FYI.

```swift
let context = AndroidContentIOSContext()!
let prefs = SHAppPrefs(androidAppApplication: context)!
```        

A special Context class 'android.content.IOSContext' that extends 'android.app.Application'
exists to be used as an Android context instance on iOS.

After that, use the AppPrefs like any other shared object.

```swift
let dog = SHDog()!

dog.setNameWith("Binky")
dog.setAgeWith(9)
dog.setLikesBelliesWithBoolean(true)

prefs.setFavoriteDogWith(dog)

let dog2 = prefs.getFavoriteDog()!

print(SHDogFactory.fromDog(with: dog2))
print(dog2.getName())
```

The android.content.SharedPreferences implementation works the same as
Android. It is actually using Android AOSP code to implement the Android
features.
