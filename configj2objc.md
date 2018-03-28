# Config J2objc

You can configure J2objc for the Gradle plugin in 2 basic ways: automatic and manual.
Just FYI, if you configure both, the plugin will fail.

## Automatic

The J2objc runtime is stock, but we package a condensed version to use that only
includes the libraries needed for the Gradle plugin to run. To config automatic
runtime management, open or create 'gradle.properties' in the project root path
and add the following:

```gradle
j2objc_runtime=2.0.6a
```

The runtimes are stored in '~/.j2objc'. If the runtime version doesn't exist locally, it'll
be downloaded automatically (it'll take a while).

### Available Versions

The Gradle plugin is compatible with stock J2objc, but not a version that's released yet.
We've created two pre-release versions: '2.0.6a' and '2.0.6b'. We are assuming the next released version will be '2.0.6'.

#### Version 2.0.6a

## Manual

You can create a local build of J2objc from source, or download a release version
(whenever 2.0.6 or later comes out. You **cannot** download a released build today
that will work with the Gradle plugin).

To configure a local J2objc runtime, find the runtime path, and add or create
the file 'local.properties' in your project's root folder. Add the following:

```gradle
j2objc.home=[runtime dist path]
```

### Where's the dist path?

If you download a distribution, the path is the folder you unzip to. If you
**build** J2objc from source, the runtime dist path is the 'dist' folder inside
the build.

### Building J2objc

Please refer to J2objc docs for more detailed instructions on building J2objc.
For the purposes of using the Gradle plugin, these steps should produce a usable
runtime.

```bash
git clone https://github.com/google/j2objc.git
cd j2objc
make -j8 frameworks
```

If that **fails** you'll need to sort out what's wrong (obviously).
