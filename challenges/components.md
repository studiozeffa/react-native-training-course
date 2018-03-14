# React Native Basics: Challenges

> Tip: start a new app with `create-react-native-app` to complete these challenges.

> Tip: when your app first loads, shake your device and choose 'Enable Live Reload'. This will ensure that your code changes are automatically applied on your device.

- Create a container `View` which fills the entire screen. Give it padding at the top to stop it covering the statusbar.
- Download the three _morpheus_ images from the [assets folder](assets/) to your computer. Create an `Image` inside your container which should display the image. Ensure it is horizontally centred.
- Below the image, add some `Text`: _This is your last chance. After this, there is no turning back. You take the blue pill — the story ends, you wake up in your bed and believe whatever you want to believe. You take the red pill — you stay in Wonderland, and I show you how deep the rabbit hole goes._.
  - The `Text` should be horizontally centred, have a vertical margin of 10, size of 18, line height of 20, colour of #311B92 and should be bold.
- Below the text, render two `TouchableHighlight` buttons, side by side (tip: use a containing `View` and the `flexDirection` style to lay them out side by side).
  - Each button should be 120 wide and 50 high, and have a margin of 10.
  - The first button should have a white coloured label _Blue Pill_ and should have a background colour of #1E88E5. When tapped, the background should change to #0D47A1.
  - The second button should have a white coloured label _Red Pill_ and should have a background colour of #F44336. When tapped, the background should change to #C62828.
  - Each label should be vertically centred inside the button.
- Render out a list of quotes:
  - Grab [this quotes JSON file](assets/quotes.json) and put it in the project directory. Use `import` to import the JSON into your app.
  - Below the buttons, add a `ScrollView` which takes up the remainder of the screen (hint: use `flex: 1` to fill available space).
  - Inside the `ScrollView`, add a `Text` component with the text _Quotes_. This should be of size 20, bold and have a bottom margin of 5.
  - Beneath _Quotes_, render each quote from the JSON file. Each quote should have a vertical margin of 5, font size of 16 and line height of 18. (Hint: use the `.map()` method to iterate over the quotes array).

## Extras

- Inside the ScrollView, above the Quotes, create a new history section with the heading _History_.
- Each time one of the buttons is pressed, add a new history item to the top of the _History_ list. Each item in the list should read _You chose the {red|blue} pill!_, depending on the pill that was chosen. (Hint: you'll need to use `state` to track the history of chosen pills)