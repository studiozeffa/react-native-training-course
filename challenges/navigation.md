# React Navigation: Challenges

> Tip: start a new app with `expo init` to complete these challenges.

> Tip: remove everything in the newly created `App.js` file before starting the below.

- Install the React Navigation library with `npm`.
- Create a new folder `/screens`, this will be the place where your screen components will live.
- Create a new component `StartScreen` and put it in the file `screens/StartScreen.js`.
- Inside StartScreen:
  - Render a `TouchableHighlight` button in the centre of the screen. It should be 200 wide and 50 high, and have a border radius of 8, with a background colour of #388E3C.
  - Inside the button, render a text label 'View Image' - this should be bold, white, of size 18 and centered in the button.
- Back in `App.js`, import the `StartScreen` component along with the two react-navigation functions `createStackNavigator` and `createAppContainer`.
- Create a new navigator by calling the `createStackNavigator()` function, passing in a configuration object. This object should include a single route to the `StartScreen`.
- Wrap this navigator in a call to `createAppContainer()` and export this navigator as the default export from `App.js`.

> At this point, you should see an app with a blank headerbar, and a single button in the centre of the screen.

- Give the `StartScreen` a headerbar title `Start`.
- Make the headerbar the same colour as the button, and the headerbar title text white.
- If you are running the app on iOS, ensure the status bar text is white (hint - put this code in `App.js` since it will affect _all_ screens).
- Create a second screen, `ImageScreen`.
- Inside this component, render an image using the URI `https://picsum.photos/400/600/?random`. Make sure the image is 200 wide, 300 high, horizontally centered and spaced vertically from the headerbar by a margin of 10.
- Give the image screen a headerbar title of `Regular Image`.
- Ensure `ImageScreen` is added to the stack navigator.
- When the button on the `StartScreen` is tapped, change its background colour to #1B5E20 (hint: use `underlayColor`), and navigate to the `ImageScreen`.

> You should now have an app which navigates from `StartScreen` to `ImageScreen`.

- Add two more buttons to the StartScreen below the first. Make sure they have a space of 10 between them.
- The second button should have the title 'View Greyscale Image'. When tapped, it should show the **same** ImageScreen with a headerbar title of `Greyscale Image` and an image with the URI `https://picsum.photos/g/400/600/?random`.
- The third button should have the title 'View Blurred Image'. When tapped, it should show the **same** ImageScreen with a headerbar title of `Blurred Image` and an image with the URI `https://picsum.photos/400/600/?random&blur`.

When you have finished, you should only have one `ImageScreen` component.

``` js
// This is correct
createStackNavigator({
  Start: StartScreen,
  Image: ImageScreen
});

// This is incorrect - find a different way
createStackNavigator({
  Start:          StartScreen,
  RegularImage:   RegularImageScreen,
  GreyscaleImage: GreyscaleImageScreen,
  BlurredImage:   BlurresImageScreen,
});
```

## Extras

- Add a button to the headerbar of the `ImageScreen` (see the [React Navigation docs](https://reactnavigation.org/docs/header-buttons.html) for more info on how to add a button to the headerbar).
  - The button should be a `TouchableOpacity`. Use an icon as the child for this buttons (see the [Expo docs](https://docs.expo.io/versions/latest/guides/icons/) regarding using icons, and choose an icon from [the directory](https://expo.github.io/vector-icons/)).
  - When the button is tapped, open an in-app browser window using the image URL that was passed in to the `ImageScreen` (use the Expo [WebBrowser](https://docs.expo.io/versions/latest/sdk/webbrowser/) to achieve this).
- Using the [documentation on modals](https://reactnavigation.org/docs/en/modal.html), add an onPress handler to the image which loads a full-width version of the image in a modal window. Ensure the modal window has a close button, which should dismiss the modal and return the user to the Image screen.
