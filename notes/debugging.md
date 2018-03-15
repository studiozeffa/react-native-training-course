## Debugging Techniques

So far, we've been running the app in _development mode_. This trades a larger app size for a faster development experience. Later, we'll discuss how to build a _production_ version of the app.

In development mode, we can gain access to the _developer menu_ by shaking the device.

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

## Yellow / Red Box notifications

In development mode, you may see a Yellow or Red Box notification.

- A Yellow Box is displayed when a warning occurs. A warning indicates that some part of your code could be modified to conform to best practices, or improve performance. These won't be displayes in production mode.
- A Red Box is displayed when your app has crashed. During development, this is normally due to a syntax error in your code. In production mode, your app will crash without a Red Box being shown.

<!-- break -->

## Further Reading

- [Debugging Guide](https://facebook.github.io/react-native/docs/debugging.html)