# React Native Setup Guide

This guide walks through how to set up your machine to develop a React Native app.

The tl;dr is:

- Install [node.js](https://nodejs.org/en/)
- (If on macOS) Install [watchman](https://nodejs.org/en/)
- Install [Google Chrome](https://www.google.com/chrome/)
- Install the [Expo mobile app](https://expo.io/) on your device
- Install the [Expo CLI](https://docs.expo.io/versions/latest/workflow/expo-cli)
- Use the Expo CLI to scaffold and start a new app
- Open the Expo app on your device and scan the QR code to reveal your new app.

<!-- break -->

## Install node.js

The first thing to do is to ensure that you have [node.js](https://nodejs.org/en/) installed. At the time of writing, node 8 is the latest stable release, and is recommended (although node 10 should work just fine as well).

You may already have watchman installed: type `node -v` in the terminal and see if it returns the version number. If you don't have node installed, [head over to the node website](https://nodejs.org/en/download/) to download and install a copy.

<!-- break -->

## Install watchman

> Note: if you aren't on a Mac, you can skip this step.

Watchman watches files for changes, and triggers an action when they do. It's used internally by the React Native development environment to auto-reload your app when you save a source file.

You may already have watchman installed: type `watchman -v` in the terminal and see if it returns the version number. If not, you'll need to go to [the watchman website](https://facebook.github.io/watchman/) to download and install it.

<!-- break -->

## Install Google Chrome

In order to connect to your app for debugging purposes, you need to use Google Chrome. If you don't have it installed, grab it from [this download page](https://www.google.com/chrome/browser/desktop/).

<!-- break -->

## Install the Expo mobile app

The Expo mobile app allows you to connect to and view your app on your mobile device, whilst it is being developed on your local machine.

To run Expo, you need one of the following devices:

- An iPhone running iOS 11 or later
- An Android phone running Android 6.0 (Marshmallow) or later

To install the app, go to the App Store or Google Play Store on your device, and search for 'Expo'. If you are reading this on your mobile device, use these links to install the [iPhone](https://itunes.apple.com/app/apple-store/id982107779?mt=8) and [Android](https://play.google.com/store/apps/details?id=host.exp.exponent) apps respectively.

<!-- break -->

## Install the Expo CLI

The [Expo CLI](https://docs.expo.io/versions/latest/workflow/expo-cli) is the easiest way to start building a new React Native application. It allows you to start a project without installing or configuring any tools to build native code.

Install it with npm:

``` bash
npm install -g expo-cli
```

All being well, you should now have installed everything you need to get started.

<!-- break -->

## Scaffold and run an app

On your local machine, open a terminal window and run:

``` bash
expo init my-sample-app
```

The CLI will ask which template to use: accept the default (blank) by pressing Enter.

> Note: if you have [yarn](https://yarnpkg.com) installed, the next prompt you will see is _Use Yarn to install dependencies?_ We are going to use npm, so press `n`.

The Expo CLI should busy itself by creating your app's development workspace, and installing all dependencies with npm. Once it is done, run:

``` bash
cd my-sample-app
npm start
```

Almost immediately, you should see a page opened in your web browser. This is the Expo Developer Tools window. Eventually, this window will present a QR code.

<!-- break -->

![Screenshot of Expo Developer Tools](/notes/assets/expo-developer-tools.png)

<!-- break -->

Now, go to your device and do the following:

- Firstly, **make sure your device is on the same WiFi network as your computer**. The Expo app needs to be able to 'see' your computer, which means they must both be on the same network.
- If you have an iPhone:
  - Open to the camera app and point the camera at the QR code.
  - A notification should appear at the top of the screen, asking if you want to open the link in the Expo app. (Note that you must have iOS 11 or later for this to work).
  - Tap the notification, the Expo app will open and will begin to load your app.
- If you have an Android phone:
  - Open the Expo app and tap the 'Scan QR code' link.
  - Point the camera at the QR code. It will scan and open your app.

<!-- break -->

## Code structure

Open up the resulting project in your code editor. You should see a few JavaScript, JSON and config files:

- `.expo/` folder - holds some configuration information for Expo. You won't need to edit anything in this folder.
- `assets/` folder: holds the icon and splashscreen images that Expo will use when you build your app for publishing to the store.
- `App.js` - the entrypoint for the app. Open this up and you'll see the sample React Native app which is created by the Expo CLI.
- `app.json` - metadata for your app. Used for various things, particularly when publishing the app to the App Store.
- `package.json` - holds a list of the direct dependencies for your app.
- `package-lock.json` - holds a complete list of all dependencies that were installed by the Expo CLI.

<!-- break -->

## Troubleshooting

### Unable to start server

If you see the following message:

```
Unable to start server
See https://git.io/v5vcn for more information, either install watchman or run the following snippet:
  sudo sysctl -w kern.maxfiles=5242880
  sudo sysctl -w kern.maxfilesperproc=524288
```

You need to install [Watchman](https://facebook.github.io/watchman/) before continuing.

<!-- break -->

### (Windows) Expo app can't connect to development server

- Ensure your computer and device are on the same network.
- If you are on Windows, and have VirtualBox or VMWare installed, `npm start` might not work properly. Try these fixes in turn:
  - [Reassign VirtualBox network interface priorities](https://github.com/react-community/create-react-native-app/issues/60#issuecomment-317104728)
  - [Allow Expo connection through the firewall](https://github.com/expo/expo/issues/438#issuecomment-352640364)

<!-- break -->

### (iPhone) Can't scan the QR code

You need iOS 11 or later in order for the QR code to be recognised by the camera.

<!-- break -->

### App is constantly reloading

If your code is located inside a folder which is synced to a cloud service (e.g. Dropbox or iCloud), when the sync occurs Expo may see your files as having changed, causing the app to constantly reload.

To solve this problem, move your code to a folder which is not synced to the cloud.

<!-- break -->

## Other Guides

Refer to the [official docs](https://facebook.github.io/react-native/docs/getting-started.html) for more information.