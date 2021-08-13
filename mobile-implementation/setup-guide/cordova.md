# Cordova

!!! abstract In this section we will walk through how you can implement and verify WOGAA tracking for your mobile application on iOS and Android.

!!! warning Do not reshare this document with anyone unless they need to implement WOGAA tracking on their mobile applications.

## Latest Version

The latest version of WOGAA Mobile Trackers is `1.4.1`.

## Overview

1. Installation
2. Implement codes for Cordova tracking
3. Check Cordova implementation
4. Verification of Cordova implementation

!!! info Cordova Tracker uses native iOS and Android Tracker underneath.

## Step 1. Installation

### Install via cordova cli

The steps to install are as follows:

```text
cordova plugin add https://github.com/wogaa/wogaa-tracker-cordova-plugin.git
```

## Step 2. Implement codes for Cordova Tracking

### Start Tracker

In your deviceready event add the start tracker

#### Staging

```javascript
window.plugins.wogaatracker.start("STAGING");
```

#### Production

```javascript
window.plugins.wogaatracker.start("PRODUCTION");
```

### Track Screen View

In each of your screen, add the following code

```javascript
window.plugins.wogaatracker.trackScreenView("Screen View Name");
```

## Step 3. Check Cordova Implementation

### Method 1: Use tool to check if data is being received in your environment\(s\).

!!! info

* Staging received events will take about 10 seconds to process. \(Last 24 hours\)
* Production received events will take about 30 minutes to process. \(Last 24 hours\)

## Step 4. Verification of Cordova Implementation

A verification email will be sent once we have successfully received data from your mobile application in production server.

It may take up to 7 working days for the verification. Please let us know if there is any issues with regards to this via wogaa@tech.gov.sg

## Reference Implementation

[https://github.com/wogaa/mobile-tracker-examples/tree/main/cordova](https://github.com/wogaa/mobile-tracker-examples/tree/main/cordova)

