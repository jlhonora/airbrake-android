Airbrake Notifer for Android
===========================

This is a fork from [loopj's implementation of airbrake for Android](https://github.com/loopj/airbrake-android). Since that library is no longer mantained, I made a couple of modifications to make it work with Android.

Overview
--------
The Airbrake notifier for Android is designed to give you instant notification
of any uncaught exceptions thrown from your Android applications.

Installation & Setup
--------------------
Copy the `AirbrakeNotifier.java` file to any of your Android app's package folder, e.g. `your.package.name`. Replace the `package` line in `AirbrakeNotifier.java` with `your.package.name`.

Import the `AirbrakeNotifier` class in your app's main Activity.

```java
import your.package.name.AirbrakeNotifier;
```

In your activity's `onCreate` function, register to begin capturing exceptions:

```java
AirbrakeNotifier.register(this, "your-api-key-goes-here");
```


Configuration
-------------
The `AirbrakeNotifier.register` call requires a context and Airbrake API key to
be passed in, and optionally a third argument specifying the environment.
The environment defaults to `production` if not set.

To notify Airbrake of non-fatal exceptions, or exceptions you have explicitly
caught in your app, you can call `AirbrakeNotifier.notify`. This call takes
exactly one argument, a Throwable, and can be called from anywhere in your
code. For example:

```java
try {
    // Something dangerous
} catch(Exception e) {
    // We don't want this to crash our app, but we would like to be notified
    AirbrakeNotifier.notify(e);
}
```


License
-------
The Airbrake notifier for Android is released under the Android-friendly
Apache License, Version 2.0. Read the full license here:

<http://www.apache.org/licenses/LICENSE-2.0>
