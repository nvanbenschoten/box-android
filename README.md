# Android box

The `nvanbenschoten/android-tablelist` box runs on ubuntu 12.04 and provides a selection of the android toolchain:

* gradle 1.12
* android sdk version 23.0.2
* android build tools 19.1 and 21
* android API 20 (android 4.4W) and 21 (android 5.0)
* sys image 19 (emulators)
* android support library

The box also inherits tools from a not yet official java box, resulting in the following additional tools:

* oracle java 7
* ant and ivy
* maven

A typical android application can use the following yaml:

``` yaml
box: nvanbenschoten/android-tablelist
# Build definition
build:
  # The steps that will be executed on build
  steps:
    - script:
        name: show base information
        code: |
          gradle -v
          echo $ANDROID_HOME
          echo $ANDROID_BUILD_TOOLS
          echo $ANDROID_UPDATE_FILTER
    # A step that executes `gradle build` command
    - script:
        name: run gradle
        code: |
          gradle --full-stacktrace -q --project-cache-dir=$WERCKER_CACHE_DIR build
```

There are a number of environment varaibles declared for your information:

* ANDROID_SDK_VERSION : version of the sdk
* ANDROID_BUILD_TOOLS : which versions of the build tools are installed.
* ANDROID_UPDATE_FILTER : shows all sdk elements which are installed

# What's new

* updated guides section

# Guides

* [Getting started with android and wercker - part 1](http://blog.wercker.com/2013/09/19/Gettingstarted-with-android-part-1.html)
* [Getting started with android and wercker - part 2](http://blog.wercker.com/2013/09/24/Gettingstarted-with-android-part-2.html)
* [Getting started with android and wercker - part 3](http://blog.wercker.com/2013/09/27/Gettingstarted-with-android-part-3.html)
* [Getting started with android and wercker - part 4](http://blog.wercker.com/2013/10/04/Getting-started-with-android-part-4.html)
* [Autoincrement versioning for android](http://blog.wercker.com/2013/10/11/auto-increment-versioning-for-android.html)

# License

The MIT License (MIT)

Copyright (c) 2013 wercker

# Changelog

## 1.0.9

* added API level 21 (android L)
* add Android buildtools 21.0.0

## 1.0.8

* added API level 20 (android 4.4W)

## 1.0.4

* updated gradle to 1.12
* updated Android SDK to 23.0.2

## 1.0.3

* add android buildtools 19.1.0

## 1.0.2

* updated gradle to 1.11

## 1.0.1

* android buildtools 19.0.1 updated to 19.0.3

## 1.0.0

* updated gradle to 1.9
* android tools 19 updated to 19.0.1 (Android 4.4.2)
* dropped: android build tools 17, 18 and android 17 api, system image for
level 18 (reason: box size)

## 0.0.19

* sys image 18

## 0.0.18

* sys image 19

## 0.0.17

* android sdk version bumped to 22.2.1
* build tools release 19 added (Android 4.4)

## 0.0.16

* switched to gradle 1.8

## 0.0.15

* $ added for environment variables in the default wercker.yml

## 0.0.14

* expanded readme.
* ANDROID_SDK_VERSION environment variable added

## 0.0.13

* initial release
