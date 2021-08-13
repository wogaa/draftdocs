# Android \(Gradle\)

!!! info As of version 1.1.4, GPS geo-location data is not captured by default and will only be derived from the IP address. You can set the geo-location enable by the `trackerConfig.setGeoLocationEnabled(true)`. To capture GPS geo-location data \(requires permission grant by user\).

!!! abstract In this section we will walk through how you can implement and verify WOGAA tracking for your mobile application on Android

!!! warning Do not reshare this document with anyone unless they need to implement WOGAA tracking on their mobile applications.

## Latest Version

The latest version of WOGAA Mobile Trackers is `1.4.1`.

## Overview

1. Install via Gradle.
2. Implement codes for Android tracking.
3. Check Android implementation
4. Verification of Android implementation

## Step 1. Install via Gradle

### Install via Gradle

[Gradle](https://gradle.org/) is an open-source build automation tool that is commonly used to manage dependencies.

!!! example "Install with Gradle" Add the following lines to your App Level Gradle build:

```text
    repositories {
      maven {
        url "https://trackers.wogaa.sg/android"
      }
    }

    dependencies {
      implementation 'sg.wogaa:tracker:1.4.+'
    }
```

## Step 2. Implement codes for Android Tracking

In your `MainActivity` class,

1. Add the following codes in `onCreate()` method or when your application starts for the appropriate environment.

!!! note "For Staging" `Tracker.start(this);`

!!! note "For Production" `Tracker.start(this, Environment.PRODUCTION);`

## Step 3. Check Android Implementation

### Method 1: Manually check the logs

#### Example

```markup
I/WOGAATracker: Started (1.4.1)
I/WOGAATracker: Sent: 1
```

!!! info `I/WOGAATracker: Started (1.4.1)` shows tracker has started and the version number of the tracker  
`I/WOGAATracker: Sent: 1` shows number of successful event\(s\) being sent to our backend system

### Method 2: Use tool to check if data is being received in your environment\(s\).

!!! info

* Staging received events will take about 10 seconds to process. \(Last 24 hours\)
* Production received events will take about 30 minutes to process. \(Last 24 hours\)

## Step 4. Verification of Android Implementation

A verification email will be sent once we have successfully received data from your mobile application in production server.

It may take up to 7 working days for the verification.

## Please let us know if there is any issues with regards to this via wogaa@tech.gov.sg

## Reference Implementation

[https://github.com/wogaa/mobile-tracker-examples/tree/main/android](https://github.com/wogaa/mobile-tracker-examples/tree/main/android)

