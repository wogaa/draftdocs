# React Native

!!! info As of version 1.1.4, GPS geo-location data is not captured by default and will only be derived from the IP address. You can set the geo-location enable by the `trackerConfig.setGeoLocationEnabled(true)`. To capture GPS geo-location data \(requires permission grant by user\).

!!! abstract In this section we will walk through how you can implement and verify WOGAA tracking for your mobile application on iOS and Android.

!!! warning Do not reshare this document with anyone unless they need to implement WOGAA tracking on their mobile applications.

## Latest Version

The latest version of WOGAA Mobile Trackers is `1.4.1`.

## Overview

1. Install via npm.
2. Implement codes for React Native tracking.
3. Check React Native implementation
4. Verification of React Native implementation

!!! info React Native Tracker uses native iOS and Android Tracker underneath.

## Step 1. Install via npm

### Install via NPM

[NPM](https://www.npmjs.com/) is an open source package manager for the JavaScript development.

!!! info npm will install React Native Tracker under `node_modules/react-native-tracker`

The steps to install are as follows:

1. `npm install https://trackers.wogaa.sg/react-native/Tracker-1.4.1.tar.gz`
2. `react-native link` \(React Native &lt; 0.60\)
3. Update `Podfile` and App level Gradle build. See examples below.

!!! example "Podfile Example" Podfile Example

```ruby
    source 'https://github.com/wogaa/Specs.git'

    target 'MasterDetailExampleApp' do
      pod 'RNTracker', :path => '../node_modules/react-native-tracker' # React Native < 0.60
      use_frameworks! # or use_modular_headers! # React Native < 0.60
    end
```

!!! example "Gradle Example" Gradle Example

```text
    repositories {
      maven {
        url "https://trackers.wogaa.sg/android"
      }
    }
```

## Step 2. Implement codes for React Native Tracking

In your `App.js` class,

1. Add `import Tracker from 'react-native-tracker';`.
2. Add the following codes when your application starts for the appropriate environment.

!!! note "For Staging" `Tracker.start("STAGING");`

!!! note "For Production" `Tracker.start("PRODUCTION");`

Add track screenview for each view.

!!! example "Track ScreenView"

```text
    componentDidMount() {
        Tracker.trackScreenView('ScreenName');
    }
```

!!! warning Please update your `Tracker.trackScreenView` to pass only the screen name as the example above. The function below had been removed because the tracker will auto generate the screen id as uuid.

```text
        Tracker.trackScreenView('ScreenId', 'ScreenName');
```

## Step 3. Check React Native Implementation

### Method 1: Manually check the logs

Run your application using Xcode or Android Studio and verify the platform logs below

#### Example \(iOS Tracker\)

```markup
[WOGAA Tracker] Started (1.4.1)
[WOGAA Tracker] Sent (1)
```

!!! info `[WOGAA Tracker] Started (1.4.1)` shows tracker has started and the version number of the tracker  
`[WOGAA Tracker] Sent (1)` shows number of successful event\(s\) being sent to our backend system

#### Example \(Android Tracker\)

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

## Step 4. Verification of React Native Implementation

A verification email will be sent once we have successfully received data from your mobile application in production server.

It may take up to 7 working days for the verification. Please let us know if there is any issues with regards to this via wogaa@tech.gov.sg

## Reference Implementation

[https://github.com/wogaa/mobile-tracker-examples/tree/main/react-native](https://github.com/wogaa/mobile-tracker-examples/tree/main/react-native)

