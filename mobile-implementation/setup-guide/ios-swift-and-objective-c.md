# iOS \(Swift and Objective-C\)

!!! info As of version 1.1.4, GPS geo-location data is not captured by default and will only be derived from the IP address. You can set the geo-location enable by the `trackerConfig.setGeoLocationEnabled(true)`. To capture GPS geo-location data \(requires permission grant by user\).

!!! abstract In this section we will walk through how you can implement and verify WOGAA tracking for your mobile application on iOS

!!! warning Do not reshare this document with anyone unless they need to implement WOGAA tracking on their mobile applications.

## Latest Version

The latest version of WOGAA Mobile Trackers is `1.4.1`. \(Compiled with Xcode 12.5\)  
WOGAA Mobile Tracker supports Swift and Objective-C for iOS.

## Overview

1. Install via CocoaPods, Carthage or Manually.
2. Implement codes for iOS tracking.
3. Check iOS implementation
4. Verification of iOS implementation

## Step 1. Install via CocoaPods, Carthage or Manually

### Method 1: Install via CocoaPods

[CocoPods](https://cocoapods.org/) is a dependency manager for Swift and Objective-C Cocoa projects.

1. Create or update your `Podfile`. \(see example below\)
2. Run `pod install`.

!!! example "Podfile Example"

```text
    source 'https://github.com/CocoaPods/Specs.git'
    source 'https://github.com/wogaa/Specs.git'

    target 'MasterDetailExampleApp' do
      pod 'Tracker', '~> 1.1'
      use_frameworks!
    end
```

### Method 2: Install via Carthage

[Carthage](https://github.com/Carthage/Carthage) is another dependency manager to add frameworks to your Cocoa application.

1. Create or update your `Cartfile`. \(see example below\)
2. Run `carthage update`.
3. Drag `Tracker.framework` in the directory `Carthage/Build/iOS` to your project.
4. Add `Tracker.framework` into your Embedded Binaries.

!!! example "Cartfile Example"

```text
    binary "https://trackers.wogaa.sg/ios/Tracker.json" ~> 1.1`
```

### Method 3: Install Manually _\(Not recommended\)_

1. Download [`Tracker-1.4.1.zip`](https://trackers.wogaa.sg/ios/Tracker-1.4.1.zip).
2. Unzip `Tracker-1.4.1.zip`.
3. Drag `Tracker.framework` into your project.
4. Add `Tracker.framework` into your Embedded Binaries.

## Step 2. Implement codes for iOS Tracking

In your `AppDelegate` class for Swift,

1. Add `import Tracker`.
2. Add the following codes in `application(:didFinishLaunchingWithOptions:)` function for the appropriate environment.

!!! note "For Staging" `Tracker.start()`

!!! note "For Production" `Tracker.start(for: .production)`

In your `AppDelegate` class for Objective-C,

1. Add `#import <Tracker/Tracker.h>`.
2. Add the following codes in `(void)applicationDidFinishLaunching:(UIApplication *)application;` function for the appropriate environment.

!!! note "For Staging" `[Tracker start];`

!!! note "For Production" `[Tracker startWith:EnvironmentProduction];`

## Step 3. Check iOS Implementation

### Method 1: Manually check the logs

#### Example

```markup
[WOGAA Tracker] Started (1.4.1)
[WOGAA Tracker] Sent (1)
```

!!! info `[WOGAA Tracker] Started (1.4.1)` shows tracker has started and the version number of the tracker  
`[WOGAA Tracker] Sent (1)` shows number of successful event\(s\) being sent to our backend system

### Method 2: Use tool to check if data is being received in your environment\(s\).

!!! info

* Staging received events will take about 10 seconds to process. \(Last 24 hours\)
* Production received events will take about 30 minutes to process. \(Last 24 hours\)

## Step 4. Verification of iOS Implementation

A verification email will be sent once we have successfully received data from your mobile application in production server.

It may take up to 7 working days for the verification. Please let us know if there is any issues with regards to this via wogaa@tech.gov.sg

## Reference Implementation

[https://github.com/wogaa/mobile-tracker-examples/tree/main/iOS](https://github.com/wogaa/mobile-tracker-examples/tree/main/iOS)

