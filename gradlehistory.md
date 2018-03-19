# Gradle Plugin History

The gradle plugin started as a fork of https://github.com/j2objc-contrib/j2objc-gradle. That plugin
uses native compilation features of gradle, which were removed (modified?) after gradle 2.8. As a
result, the plugin limits you to gradle 2.8, which is basically a non-starter for Android development.

We forked the original gradle plugin, then did a bunch of modifications over the last ~2 years.
Our J2objc version was slightly modified, so the whole thing was under a different name (Doppl).

Over the past few months, effort to get back into the J2objc mainline have resulted in a
stock gradle plugin. There's nothing custom about the J2objc build. As a result, having a
different name for the Gradle plugin doesn't make much sense, so "Doppl Gradle" became "J2objc Gradle".

We're going to reach out to the j2objc-contrib team and see if it makes sense to push the plugin to that
org instead, but although this is a fork of that, and they're philosophically similar, they are at this
point very different in operation. On the other hand, 2 "j2objc-gradle" projects will get confusing. TBD.

## Doppl?

Doppl is going to exist as a separate github org. The libraries there are less "stock" Java. There are extended
Android-specific architectural libraries, the idea of which is to replicate significantly more architecture between
platforms. Those libraries have been updated to use this plugin. The name "Doppl" is going to be used
for libraries that are implementing Android architecture on iOS, and the github order will be a more experimental
place.
