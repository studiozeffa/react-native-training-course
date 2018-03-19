## Navigating Between Screens

Mobile apps use a navigation 'stack' to navigate between pages. The concept is similar to the browser:

- To navigate to a new screen, a page is 'pushed' onto the stack, adding to the navigation history.
- You can go back to the previous page by 'popping' a page off the stack.

Each platform has established patterns to achieve this.

<!-- break -->

### iOS

A new screen is pushed onto the stack, with the screen revealing from the right hand side of the screen.

A _Back_ button appears in the left hand side of the headerbar, to go back. You can also swipe from the left hand side of the display to achieve this.

### Android

A new screen is pushed, with the screen appearing with a gentle fade-in animation from the bottom of the screen.

A _Back_ button appears in the left hand side of the headerbar, to go back. You can also press the hardware back button to achieve this.

<!-- break -->

## React Navigation

The [React Navigation](https://reactnavigation.org) library applies these navigation patterns for use in a React Native app.

It is a third party dependency, install it with `yarn`:

```
  yarn add react-navigation
```

Using this library, set up a `StackNavigator`, which defines the different screens to navigate between. Each screen will be created as a separate React component.

Each screen will be rendered with a headerbar, and will also receive a `navigation` prop, which can be used to navigate to different pages.

<!-- break -->

### React Navigation Example

``` jsx
import React from 'react';
import { View, Text } from 'react-native';
import { StackNavigator } from 'react-navigation';

const HomeScreen = () => (
  <View><Text>This is the Home Screen!</Text></View>
);

const InfoScreen = () => (
  <View><Text>This is the Info Screen!</Text></View>
);

const RootNavigator = StackNavigator({
  Home: HomeScreen,
  Info: InfoScreen
});

export default RootNavigator;
```

<!-- break -->

## Controlling the headerbar

The headerbar can be controlled via a `navigationOptions` property on the component.

Use this to set the headerbar title, style and buttons.

``` jsx
const HomeScreen = () => (
  /* ... */
);

HomeScreen.navigationOptions = {
  title: 'Home',
  headerStyle: {
    backgroundColor: '#68aa63'
  },
  headerTintColor: '#ffffff'
}
```

<!-- break -->

## Navigating Between Screens

Each screen configured inside a `StackNavigator` will be passed a `navigation` prop.

Use this to navigate to a new screen:

``` jsx
import React, { Component } from 'react';
import { View, Button } from 'react-native';

class HomeScreen extends Component {
  onPress() {
    this.props.navigation.navigate('InfoScreen');
  }

  render() {
    return <Button title="Info Screen" onPress={this.onPress} />;
  }
}
```

<!-- break -->

## Passing data to screen

Pass an object as the second argument to `navigate` to send data to the screen. Pull it out with `state.params`:

``` jsx
class HomeScreen extends Component {
  onPress() {
    this.props.navigation.navigate('InfoScreen', {
      body: 'This is the Info Screen'
    });
  }
}

class InfoScreen extends Component {
  render() {
    const { body } = this.props.navigation.state.params;
    return <Text>{body}</Text>;
  }
}
```

<!-- break -->

## Passing headerbar data to screen

You can use the function form of `navigationOptions` to access the `navigation` object for use by the headerbar:

``` jsx
class HomeScreen extends Component {
  onPress() {
    this.props.navigation.navigate('InfoScreen', {
      title: 'Info'
    });
  }
}

class InfoScreen extends Component {}

InfoScreen.navigationOptions = ({navigation}) => ({
  title: navigtion.state.params.title
})
```

<!-- break -->

## Further Reading

- [React Navigation Docs](https://reactnavigation.org/docs/getting-started.html)