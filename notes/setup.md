# React Native Setup Guide

This guide walks through how to set up your machine to develop a React Native app.

The tl;dr is:

- Install [node.js](https://nodejs.org/en/)
- Install [watchman](https://nodejs.org/en/)
- Install [yarn](https://yarnpkg.com/)
- Install [Google Chrome](https://www.google.com/chrome/)
- Install the [Expo mobile app](https://expo.io/) on your device
- Install [Create React Native App](https://github.com/react-community/create-react-native-app)
- Use Create React Native App to scaffold and start a new app
- Open Expo and scan the QR code to reveal your new app.

<!-- break -->

## Install node.js

The first thing to do is to ensure that you have [node.js](https://nodejs.org/en/) installed. At the time of writing, node 8 is the latest stable release, and is recommended (although node 10 should work just fine as well).

You may already have watchman installed: type `node -v` in the terminal and see if it returns the version number. If you don't have node installed, [head over to the node website](https://nodejs.org/en/download/) to download and install a copy.

<!-- break -->

## Install watchman

Watchman watches files for changes, and triggers an action when they do. It's used internally by the React Native development environment to auto-reload your app when you save a source file.

You may already have watchman installed: type `watchman -v` in the terminal and see if it returns the version number. If not, you'll need to go to [the watchman website](https://facebook.github.io/watchman/) to download and install it.

<!-- break -->

## Install yarn

React Native supports both npm4 and yarn. Node 8, however, ships with npm5 - this is currently unsupported. To get around this, we'll use [yarn](https://yarnpkg.com/), which is generally faster and more reliable than any version of npm.

You may already have yarn installed: type `yarn -v` in the terminal and see if it returns the version number. If not, to install yarn, [go to the download page](https://yarnpkg.com/en/docs/install) and find the installation instructions for your OS.

<!-- break -->

## Install Google Chrome

In order to connect to your app for debugging purposes, you need to use Google Chrome. If you don't have it installed, grab it from [this download page](https://www.google.com/chrome/browser/desktop/).

## Install the Expo mobile app

The Expo mobile app allows you to connect to and view your app on your mobile device, whilst it is being developed on your local machine.

To install it, go to the App Store or Google Play Store on your device, and search for 'Expo'. If you are reading this on your mobile device, use these links to install the [iPhone](https://itunes.apple.com/app/apple-store/id982107779?mt=8) and [Android](https://play.google.com/store/apps/details?id=host.exp.exponent) apps respectively.

<!-- break -->

## Install Create React Native App

[Create React Native App](https://github.com/react-community/create-react-native-app) is the easiest way to start building a new React Native application. It allows you to start a project without installing or configuring any tools to build native code.

Install it with npm:

``` bash
npm install -g create-react-native-app
```

All being well, you should now have installed everything you need to get started.

<!-- break -->

## Scaffold and run an app

On your local machine, open a terminal window and run:

``` bash
create-react-native-app my-sample-app
```

Create React Native App should busy itself by creating your app's development workspace, and installing all dependencies with yarn. Once it is done, run:

``` bash
cd my-sample-app
yarn start
```

Wait a couple of minutes for the server to start, and then you should see a QR code presented in the terminal.

Now, go to your device and do the following:

- If you have an iPhone:
  - Open to the camera app and point the camera at the QR code.
  - A notification should appear at the top of the screen, asking if you want to open the link in the Expo app.
  - Tap the notification, the Expo app will open and will begin to load your app.
- If you have an Android phone:
  - Open the Expo app and tap the 'Scan QR code' link.
  - Point the camera at the QR code. It will scan and open your app.

<!-- break -->

## Code structure

Open up the resulting project in your code editor. You should see a few JavaScript, JSON and config files. Here's a summary of the important ones:

- `App.js` - the entrypoint for the app. Open this up and you'll see the sample React Native app which is created by the `create-react-native-app` tool.
- `app.json` - metadata for your app. Used for various things, particularly when publishing the app to the App Store.
- `package.json` - holds a list of the dependencies for your app.
- `App.test.js` - you can run unit tests on a React Native app using a tool called [Jest](https://facebook.github.io/jest/). The convention is to name test files with the `.test.js` suffix. We won't be covering testing on this course.

<!-- break -->

## Troubleshooting

### (Windows) Expo app can't connect to development server

- Ensure your computer and device are on the same network.
- If you are on Windows, and have VirtualBox or VMWare installed, `yarn start` might not work properly. [Follow these instructions to solve](https://github.com/react-community/create-react-native-app/issues/60#issuecomment-317104728).

### (Mac) Unable to start server

If you see the following message:

```
Unable to start server
See https://git.io/v5vcn for more information, either install watchman or run the following snippet:
  sudo sysctl -w kern.maxfiles=5242880
  sudo sysctl -w kern.maxfilesperproc=524288
```

You need to install [Watchman](https://facebook.github.io/watchman/) before continuing.

<!-- break -->

## Other Guides

Refer to the below to see some alternative setup instructions. They all follow the same general pattern as above but may offer additional help.

- [Official Docs](https://facebook.github.io/react-native/docs/getting-started.html)
- [React Native Express](http://www.reactnativeexpress.com/quick_start)