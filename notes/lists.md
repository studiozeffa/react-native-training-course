## React Native: List/Detail View

Many apps conform to a 'list/detail' pattern:

- A list of items is presented on the first screen, with a summary of information (usually a title and optional subtitle).
- Each list item is tappable.
- When tapped, the app navigates to a detail view, showing data from the corresponding item that was tapped.

<!-- break -->

### List/Detail View Example

```
        List:                  Detail:
     ____________            ____________
    /            \          /            \
    | Item       |          | Title      |
    | ---------- |          | Subtitle   |
    | Item    ●--|------>   |            |
    | ---------- |          | Here is a  |
    | Item       |          | house.     |
    | ---------- |          |            |
    | Item       |          |   []___    |
    | ---------- |          |  /    /\   |
    | Item       |          | /____/__\  |
    | ---------- |          | |[][]||||  |
    | Item       |          |            |
    \____________/          \____________/

```

<!-- break -->

## Lists

One way to implement the list is to use a `ScrollView` with many individual `View` items:

``` jsx
return (
  <ScrollView>
    <View><Text>1</Text></View>
    <View><Text>2</Text></View>
    <View><Text>3</Text></View>
    <View><Text>4</Text></View>
  </ScrollView>
);
```

<!-- break -->

### Lists: mapping

Taking this a step further, instead of repeating the JSX we could use an array and `map` over it:

``` jsx
const items = ['Item 1', 'Item 2', 'Item 3', 'Item 4'];
return (
  <ScrollView>
    {items.map((item, index) => (
      <View key={index}><Text>{item}</Text></View>
    ))}
  </ScrollView>
);
```

<!-- break -->

## FlatList

When rendering a list of items, a better alternative to `ScrollView` is available: `FlatList`.

``` jsx
import React, { Component } from 'react';
import { View, Text, FlatList } from 'react-native';

class List extends Component {
  renderItem({item}) {
    return <View><Text>{item}</Text></View>;
  }

  render() {
    const items = ['Item 1', 'Item 2', 'Item 3', 'Item 4'];
    return <FlatList data={items} renderItem={this.renderItem} />;
  }
}
```

<!-- break -->

### keyExtractor

Similar to a `ScrollView`, each item in the `FlatList` needs a key:

``` jsx
import React, { Component } from 'react';
import { View, Text, FlatList } from 'react-native';

class List extends Component {
  keyExtractor(item, index) {
    return index;
  }

  render() {
    const items = ['Item 1', 'Item 2', 'Item 3', 'Item 4'];
    return (
      <FlatList data={items} keyExtractor={this.keyExtractor} />
    );
  }
}
```
<!-- break -->

### ItemSeparatorComponent

Use `ItemSeparatorComponent` to render a separator between each item:

``` jsx
import React, { Component } from 'react';
import { View, Text, FlatList } from 'react-native';

class List extends Component {
  renderSeparator() {
    const style = { height: 1, backgroundColor: '#777' };
    return <View style={style} />;
  }

  render() {
    return (
      <FlatList ItemSeparatorComponent={this.renderSeparator} />
    );
  }
}
```

<!-- break -->

## Text truncation

Sometimes, you don't want `Text` to wrap when it reaches the end of its container. This is especially true when rendering list items.

You can use the `numberOfLines` prop to truncate text after a specific number of lines.

``` jsx
return (
  <Text numberOfLines={1}>
    Laboris in ea fugiat nisi exercitation ipsum elit incididunt
    fugiat cupidatat in. Tempor nisi sint ad non excepteur mollit
    sint adipisicing. Laborum ut et culpa dolore elit eiusmod
    laborum in ullamco qui qui elit sunt.
  </Text>
);
```

The text will be truncated, and ellipses will be added (`...`).

<!-- break -->

## Platform-specific code

Sometimes we want to conditionally run code depending on the target platform (iOS / Android). We can achieve this using the `Platform` module.

``` js
import { Platform } from 'react-native';

const isIOS = Platform.OS === 'ios';
const isAndroid = Platform.OS === 'android';
```

<!-- break -->

## Platform-specific styles

Oftentimes we also want to change styles according to the platform. This is possible with `Platform.select()`:

``` js
import { Platform } from 'react-native';

const platformStyles = Platform.select({
  ios: {
    backgroundColor: '#fff'
  },
  android: {
    backgroundColor: '#eee'
  }
});

console.log(platformStyles);
// -> on iOS: { backgroundColor: '#fff' }
// -> on Android: { backgroundColor: '#eee' }
```

<!-- break -->

### Applying the styles

We can then apply the styles to a `StyleSheet` using the Object spread syntax:

``` js
import { StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    flex: 1,
    // Spread the platformStyles object into this one
    ...platformStyles
  }
});
```

<!-- break -->

### Results

The above will produce the following styles on iOS:

``` js
{
  flex: 1,
  backgroundColor: '#fff'
}
```

and the following on Android:

``` js
{
  flex: 1,
  backgroundColor: '#eee'
}
```

<!-- break -->

## Third Party Libraries

Since much of React Native runs as JavaScript, we can use any JavaScript-based library, provided it does not use any browser APIs.

Install a third party library with `yarn`:

``` bash
yarn add moment
```

Then import the library for use as normal:

``` jsx
import React from 'react';
import { Text } from 'react-native';
import moment from 'moment';

const RightNow = ({date}) => (
  <Text>{moment(date).calendar()}</Text>
);
```

<!-- break -->

## Further Reading

- [FlatList](https://facebook.github.io/react-native/docs/flatlist.html)
- [Platform Specific Code](https://facebook.github.io/react-native/docs/platform-specific-code.html)

### Useful third party modules

- [Lodash](https://lodash.com)
- [Moment](https://moment.com)
- [React Navigation](https://reactnavigation.org)
- [Redux](https://redux.js.org/), [React Redux](https://github.com/reactjs/react-redux) and [Redux Persist](https://github.com/rt2zz/redux-persist)
- [Collection of React Native components](http://www.awesome-react-native.com/#components)