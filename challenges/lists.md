# List/Detail Pattern: Challenges

> Tip: start a new app with `create-react-native-app` to complete these challenges.

- Use React Navigation to create two screens: `List` and `Detail`. Add a button to navigate from list -> detail. Use the following configuration:
  - Give the List screen a headerbar title of 'Contacts'
  - Make sure the headerbar has a background colour of #bc4812, with white text. If you are on iOS, don't forget the statusbar text colour too.
- Pull down the list of contacts from [here](TBCTBCTBC) and put it into your project filesystem.
- Import the contacts in your `List` screen.
- Use FlatList to render each contact in the `List`. Each item should:
  - have a height of 40
  - display the contact name on a single line with size 18 font, padded from the left/right hand side of the screen by 10
  - have a background colour of '#e9e9e9', changing to '#ddd' when tapped
  - be separated from other items with a line, of height 1 and colour '#aaa'
- When an item is tapped in the `List`, navigate to the `Detail` view. Here, render the contact's avatar, name, age, address and workplace.

> The final app should resemble the following:

******* TBC ********

## Extras

- Modify the FlatList item to include the contact's avatar and age. The age should be displayed below the name, with the avatar to the left of both.
- Add a chevron to the right hand side of the list item, but only on iOS:
  - Use the [expo vector icons](https://docs.expo.io/versions/latest/guides/icons.html#expovector-icons) package, and search for the appropriate icon to use.
  - Ensure the icon is vertically centered inside the item, is coloured #777 and has a size of 16.
- Add an icon to the headerbar of the Detail view. When the icon is tapped, open the [Expo WebBrowser](https://docs.expo.io/versions/latest/sdk/webbrowser.html) with the URL of the contact's favourite film. (Hint: use a `TouchableOpacity`, and check out the [React Navigation docs](https://reactnavigation.org/docs/header-buttons.html) for an example of headerbar buttons).
- Use the [react-native-parallax-scroll-view](https://github.com/i6mi6/react-native-parallax-scroll-view) package to create a parallax effect on the contact's avatar when scrolling.
