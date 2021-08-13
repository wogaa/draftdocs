# Custom Screenview Tracking

## Overview

WOGAA tracks screen transitions and attaches information about the current screen to the events, enabling you to track how your users engage different parts of your app.

Much of this data collection happens automatically, but it may not be in the form which easy for a non-technical user to understand as these names are usually names given within the code.

Manually tracking screens is useful also if your app do not use a seperate `UIViewController` or `Activity` for each screen you may wish to track.

## Automatic screen tracking

WOGAA automatically tracks some information about screens in your application that is currently in focus.

When a screen transition occurs, WOGAA logs a `screenview` event that identifies a transition to a new screen. Events that occur on these screens are automatically tagged with a generated unique id to be associated with the `screenview` event and the `viewController`, `topViewController` \(iOS specific\) and `activity`, `fragment` \(Android specific\).

## Manual screen tracking

In certain cases, you may manually set the screen name and optionally override the class name when screen transitions occur to have more granular control on what is being tracked.

### Benefits of Manual screen tracking

Manually setting screen names has many benefits:

* Have more user friendly names that can be recognised by users analyzing these data
* Unify naming convention across platforms \(i.e. Android & iOS\) to help better collate your overall app traffic usage for specific screens

### Implementating manual screenview tracking

The accepted arguments are:

| Argument | Description | Required? | Type |
| :--- | :--- | :--- | :--- |
| `ScreenName` | Human-readable name for this screen | No | `String` |

The following example shows how to manually set the screen name.

!!! example "Android-Java"

```java
    Tracker.trackScreenView("ScreenName");
```

!!! example "Android-Kotlin"

```java
    Tracker.trackScreenView("ScreenName");
```

!!! example "Swift"

```text
    Tracker.trackScreenView("ScreenName");
```

!!! example "Objective-C"

```text
    [Tracker trackScreenViewWith: "ScreenName"]
```

!!! example "React Native"

```javascript
    Tracker.trackScreenView('DetailScreen');
```

!!! example "Flutter"

```dart
    Tracker.trackScreenView('ScreenName');
```

!!! warning Please update your `Tracker.trackScreenView` to pass only the screen name same as the example above. The function below had been removed because the tracker will auto generate the screen id as uuid.

```text
        Tracker.trackScreenView('ScreenId', 'ScreenName');
```

