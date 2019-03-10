## Running the app on your computer

Mobile apps are built to run on mobile devices. You should always be testing the app on real devices.

Using a mobile device during development can be cumbersome, however. Apple and Google realise this, and so offer methods for running the app on your computer during development.

We'll briefly introduce these here - feel free to install and use these tools for the remainder of this course.

<!-- break -->

## iOS simulator

Available with Xcode, the iOS simulator allows you to run an iOS app during development on your Mac (sorry Windows/Linux users - this is only available on a Mac).

The majority of features available in iOS are present in the simulator, with a few notable exceptions (camera, telephony, etc).

To use it, you need to download and install Xcode. The easiest way to do this is via the [Mac App Store](https://itunes.apple.com/app/xcode/id497799835).

<!-- break -->

## Android emulator

This tool is available via Android Studio, and allows you to run an Android app on your computer. Unlike the iOS simulator, the Android emulator is available on all platforms.

To get set up, follow [this handy guide from Expo](https://docs.expo.io/versions/latest/workflow/android-studio-emulator/).

<!-- break -->

## Debugging Techniques

So far, we've been running the app in _development mode_. This trades a larger app size for a faster development experience. Later, we'll discuss how to build a _production_ version of the app.

In development mode, we can gain access to the _developer menu_ by shaking the device (or pressing `Cmd-D` in the simulator).

This menu provides us with many options. We'll be discussing two of them:

- Live Reloading
- Debugging JS Remotely

<!-- break -->

## Live Reloading

Selecting the option _Enable Live Reload_ will automatically reload the app whenever any changes are saved in your text editor.

There is also another option: _Enable Hot Reloading_. This is supposed to apply changes without needing to reload the app. This feature does not work reliably and often causes the app to crash, so it's not currently recommended for use.

<!-- break -->

## Debug JS Remotely

Selecting the option _Debug JS Remotely_ will reload the app and open Google Chrome on your laptop.

You can now use the Google Chrome Developer Tools to step through the JavaScript code in your React Native app, as you would do for a regular web application.

<!-- break -->

## React Native Debugger

An alternative, superior option for debugging is with a tool called [React Native Debugger](https://github.com/jhen0409/react-native-debugger).

This provides access to the Chrome, React and Redux DevTools, all in one window.

- When starting for the first time, go to Debugger -> New Window and open a new window on port 19001.
- Then, shake your device and choose 'Toggle Inspector'. This allows you to inspect your views in the React DevTools.

<!-- break -->

## Yellow / Red Box notifications

In development mode, you may see a Yellow or Red Box notification.

- A Yellow Box is displayed when a warning occurs. A warning indicates that some part of your code could be modified to conform to best practices, or improve performance. These won't be displayed in production mode.
- A Red Box is displayed when your app has crashed. During development, this is normally due to a syntax error in your code. In production mode, your app will crash without a Red Box being shown.

<!-- break -->

## Further Reading

- [Debugging Guide](https://facebook.github.io/react-native/docs/debugging.html)
