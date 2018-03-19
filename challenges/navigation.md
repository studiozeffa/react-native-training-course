# React Navigation: Challenges

> Tip: start a new app with `create-react-native-app` to complete these challenges.

> Tip: remove everything in the newly created `App.js` file except the `import React from 'react'` before starting the below.

- Install the React Navigation library with `yarn`.
- Create a new component `StartScreen`. Render a `TouchableHighlight` button in the centre of the screen. It should be 200 wide and 50 high, and have a border radius of 8, with a background colour of #388E3C, and contain white bold text which reads 'View Image'.
- Create a new `StackNavigator`, configured to show this `StartScreen`.
- Export a stateless function component `App`, which renders the created navigator.

> At this point, you should see an app with a blank headerbar, and a single button in the centre of the screen.

- Give the `StartScreen` the title `Start`.
- Make the headerbar the same colour as the button, and the headerbar text white.
- Create a second component, `ImageScreen`. Inside this component, render an image using the URI `https://picsum.photos/400/600/?random`. Make sure the image is 200 wide, 300 high, horizontally centered and spaced vertically from the headerbar by a margin of 10.
- Give the image screen a headerbar title of `Regular Image`.
- When the button on the `StartScreen` is tapped, change its background colour to #1B5E20, and navigate to the `ImageScreen`.

> You should now have an app which navigates from `StartScreen` to `InfoScreen`.

- Add two more buttons to the StartScreen below the first. Make sure they have a space of 10 between them.
- The second button should have the title 'View Greyscale Image'. When tapped, it should show the ImageScreen with a headerbar title of `Greyscale Image` and an image with the URI `https://picsum.photos/g/400/600/?random`.
- The third button should have the title 'View Blurred Image'. When tapped, it should show the ImageScreen with a headerbar title of `Blurred Image` and an image with the URI `https://picsum.photos/400/600/?random&blur`.
