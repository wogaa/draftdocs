# Flutter

!!! abstract In this section we will walk through how you can implement and verify WOGAA tracking for your mobile application on Flutter

!!! warning Do not reshare this document with anyone unless they need to implement WOGAA tracking on their mobile applications.

## Latest Version

The latest version of WOGAA Mobile Trackers is `1.0.2`.

## Overview

1. Install via pubspec
2. Implement codes for Flutter tracking
3. Check Flutter implementation
4. Verification of Flutter implementation

## Step 1. Install via pubspec

### Install via pubspec

[Pubspec](https://flutter.dev/docs/development/tools/pubspec) is a dependency manager for Flutter.

1. Create or update your `pubspec.yaml`, add wogaa tracker package in the `dependencies` section. \(see example below\)
2. Run `flutter pub get`.

!!! example "Podfile Example"

```text
    dependencies:
        wogaa_flutter_tracker:
            git:
                url: https://github.com/wogaa/wogaa_flutter_tracker.git
                ref: v1.0.2
```

## Step 2. Implement codes for Flutter Tracking

In your `main.dart` class,

1. Add `import 'package:wogaa_flutter_tracker/wogaa_flutter_tracker.dart';`.
2. Add the following codes when your application starts for the appropriate environment.

!!! note "For Staging" `Tracker.start();`

!!! note "For Production" `Tracker.start('production');`

Add track screenview for each view.

!!! example "Track ScreenView"

```text
    Tracker.trackScreenView('ScreenName');
```

## Step 3. Check Flutter Implementation

### Method 1: Manually check the logs

#### Example

```markup
Flutter: Started (1.0.2)
Flutter: Sent (1)
```

!!! info `Flutter: Started (1.0.2)` shows tracker has started and the version number of the tracker  
`Flutter: Sent (1)` shows number of successful event\(s\) being sent to our backend system

### Method 2: Use tool to check if data is being received in your environment\(s\).

!!! info

* Staging received events will take about 10 seconds to process. \(Last 24 hours\)
* Production received events will take about 30 minutes to process. \(Last 24 hours\)

## Step 4. Verification of Flutter Implementation

A verification email will be sent once we have successfully received data from your mobile application in production server.

It may take up to 7 working days for the verification. Please let us know if there is any issues with regards to this via wogaa@tech.gov.sg

## Reference Implementation

[https://github.com/wogaa/wogaa\_flutter\_tracker/tree/master/example](https://github.com/wogaa/wogaa_flutter_tracker/tree/master/example)

