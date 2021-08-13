# Xamarin

!!! abstract In this section we will walk through how you can implement and verify WOGAA tracking for your mobile application on iOS and Android.

!!! warning Do not reshare this document with anyone unless they need to implement WOGAA tracking on their mobile applications.

## Dependencies

1. Visual Studio
2. Xamarin Form
3. LiteDB 3.1.0 
4. Snowplow Tracker 1.0.2
5. Snowplow Tracker PlatformExtensions 1.0.2
6. Android SDK API 16 and above
7. Target Framwork 9.0

!!! info Xamarin Tracker uses Snowplow DotNet Trackers.

## Step 1. Install dependencies

### Install Xamarin Form

1. Open Manage NuGet Packages
2. Search for `Xamarin Form`
3. Select `Xamarin Form`
4. Click Install Package
5. Check for both iOS and Android

### Install LiteDB

1. Open Manage NuGet Packages
2. Search for `LiteDB`
3. Select `LiteDB` with version `3.1.0`
4. Click Install Package
5. Check for both iOS and Android

### Install Snowplow Tracker

1. Open Manage NuGet Packages
2. Search for `Snowplow Tracker`
3. Select `Snowplow Tracker`
4. Click Install Package
5. Check for both iOS and Android

### Install Snowplow Tracker PlatformExtensions

1. Open Manage NuGet Packages
2. Search for `Snowplow Tracker PlatformExtensions`
3. Select `Snowplow Tracker`
4. Click Install Package
5. Check for both iOS and Android

## Step 2. Configure project setting

1. Righ click Android project
2. Select Options
3. Select General
4. At Target Framework select Android 9.0\(Pie\)
5. Click Ok

## Step 3. Implement codes for Xamarin tracking

### Wogaa Tracker

1. Copy [WogaaTracker.cs](../../sample-codes/xamarin/WogaaTracker.cs) to the main project directory.
2. Update the namespace in `WogaaTracker.cs` - `MultieplatformApp` to your project namespace.

#### iOS

!!! note "Xamarin Native" Add the following code into AppDelegate.cs `FinishedLaunching` function after `App.Initialize()`

!!! note "Xamarin Form" Add the following code into AppDelegate.cs `FinishedLaunching` function before `LoadApplication(new App())`

```text
if (!Snowplow.Tracker.Tracker.Instance.Started)
{
    WogaaTracker.Init(url: WogaaTracker.ENVIRONMENT.staging);
}
```

Add the following code into AppDelegate.cs `WillTerminate` function

```text
WogaaTracker.Shutdown();
```

Add following code to all `ViewController` into `ViewDidAppear` function, and replace the `Screen Name` to your actual screen name.

```text
 WogaaTracker.TrackScreenView("Screen Name");
```

#### Android

!!! note "Xamarin Native" Add the following code into MainApplication.cs `OnCreate` function after `App.Initialize()`

!!! note "Xamarin Form" Add the following code into MainApplication.cs `OnCreate` function before `LoadApplication(new App())`

```text
if (!Snowplow.Tracker.Tracker.Instance.Started)
{
    WogaaTracker.Init(
    url: WogaaTracker.ENVIRONMENT.staging,
    userAgent: Android.Webkit.WebSettings.GetDefaultUserAgent(Application.Context));
}
```

!!! note "Xamarin Native" Add the following code into MainApplication.cs `OnTerminate` function

!!! note "Xamarin Form" Add the following code into MainApplication.cs `OnDestroy` function

```text
WogaaTracker.Shutdown();
```

Add following code to all `Activity` into `OnCreate` function, and replace the `<<Screen Name>>` to your actual screen name.

```text
 WogaaTracker.TrackScreenView("Screen Name");
```

## Step 4. Check Xamarin implementation

### Method 1: Manually check the logs

Run your application using Xcode or Android Studio and verify the platform logs below

#### iOS

```markup
Info: Emitter flushed all (1) events successfully
```

!!! note `Info: Emitter flushed all (1) events successfully` shows number of successful event\(s\) being sent to our backend system

#### Android

```markup
Info: Emitter sent and deleted 1 events
```

!!! note `Info: Emitter sent and deleted 1 events` shows number of successful event\(s\) being sent to our backend system

### Method 2: Use tool to check if data is being received in your environment\(s\).

!!! info

* Staging received events will take about 10 seconds to process. \(Last 24 hours\)
* Production received events will take about 30 minutes to process. \(Last 24 hours\)

## Step 4. Verification of Xamarin Implementation

### Move to Production

Change the Environment variable from `Staging` to `Production`.

```text
WogaaTracker.ENVIRONMENT.Production
```

A verification email will be sent once we have successfully received data from your mobile application in production server.

It may take up to 7 working days for the verification. Please let us know if there is any issues with regards to this via wogaa@tech.gov.sg

## Reference Implementation

[https://github.com/wogaa/mobile-tracker-examples/tree/main/xamarin](https://github.com/wogaa/mobile-tracker-examples/tree/main/xamarin)

