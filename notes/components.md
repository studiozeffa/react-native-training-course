## React Native Components

A React Native app is simply a React app with a collection of custom components and APIs, which renders as a native mobile app instead of to the browser.

Many of these components are inspired by the web (e.g. `View`, `Text`, `Image`). Since they are custom components, they must be imported for use:

``` js
import { View, Text, StyleSheet } from 'react-native';
```

APIs are used to create stylesheets, access hardware sensors (camera, accelerometer, etc) and conditionally execute code on specific platforms.

<!-- break -->

## View

A `View` is like a `div`. Use it as a generic container, which can:

- be styled
- hold other components

``` jsx
const style = { /* ... */ };
return (
  <View style={style}>
    <Text>I'm inside a View!</Text>
  </View>
)
```

<!-- break -->

## Styles and StyleSheet

Styles are used to lay out and apply visual styles to a component. They are applied to components using the `style` attribute. A `StyleSheet` can be used to collect a group of styles.

One big difference to CSS is that React Native styles almost never cascade (that is, child components do not inherit styles applied to their parents). The one exception here is nested `Text` components.

Style notation is heavily inspired by CSS, using `camelCase` instead of `kebab-case`. Mostly, think of the CSS property you want to apply, and make it `camelCase`.

<!-- break -->

## Layout

Layout is governed by a system known as 'Yoga', which is very similar to flexbox.

The one big exception is that it lays out neighbouring components in a column, rather than a row (i.e. `flexDirection` defaults to `'column'`).

Use `flex: 1` on the root `View` container to ensure that the app fills the entire screen.

<!-- break -->

### Styles example

``` jsx
const styles = StyleSheet.create({
  boxes: {
    flexDirection: 'row'  // Use flexbox to lay things out
  },
  box: {
    // Dimensions are numbers instead of px or em
    height: 100, width: 100, margin: 10,
    backgroundColor: 'firebrick'
  }
});

return (
  <View style={styles.boxes}>
    <View style={styles.box} />
    <View style={styles.box} />
  </View>
);
```

<!-- break -->

## Multiple Styles

You can apply multiple styles to a component using an array:

``` jsx
const styles = StyleSheet.create({
  box: {
    height: 100, width: 100, margin: 10
  },
  boxPrimary: { backgroundColor: 'firebrick' },
  boxSecondary: { backgroundColor: 'seagreen' }
});

return (
  <View style={styles.boxes}>
    <View style={[styles.box, styles.boxPrimary]} />
    <View style={[styles.box, styles.boxSecondary]} />
  </View>
);
```

<!-- break -->

## Dynamic Styles

Sometimes you need to add dynamic styles to a component, e.g. based on a prop.

Use `StyleSheet.create` outside your component for static styles, and apply any dynamic styles inside the render method:

``` jsx
const styles = StyleSheet.create({
  box: {
    height: 100, width: 100, margin: 10
  }
});

const Box = ({ color }) => (
  <View style={[styles.box, { backgroundColor: color } ]} />
);
```

<!-- break -->

## Text

`Text` is used to render a set of characters to the screen.

Unlike all other components, `Text` will wrap when it reaches the end of its container. Styles will also cascade to child `Text` components.

Each platform has a predefined set of built-in fonts that can be used. You can also add custom fonts, similar to the web.

``` jsx
const style = { fontSize: 18, color: 'brown' };
return (
  <Text style={style}>
    The quick brown fox jumped over the lazy dog.
  </Text>
);
```

<!-- break -->

## ScrollView

Unlike the web, a regular `View` will not become scrollable when its content overflows the container.

We must use a `ScrollView` to achieve this.

``` jsx
return (
  <ScrollView>
    <Text>Laboris in ea fugiat nisi exercitation ipsum elit
    incididunt fugiat cupidatat in. Tempor nisi sint ad non
    excepteur mollit sint adipisicing. Laborum ut et culpa
    dolore elit eiusmod laborum in ullamco qui qui elit sunt.
    </Text>
  </ScrollView>
);
```

<!-- break -->

## Local Images

An `Image` component is used to render an image, either stored locally within the app, or from a remote URL.

Local images must be `import`ed:

``` jsx
import image from './resources/image.png';
return <Image source={image} />
```

To support high resolution displays, provide three versions of each image, at 1x, 2x and 3x sizes. Name the images as follows - React Native will choose the best one automatically:

- Original (1x) size: `image.png`
- 2x size: `image@2x.png`
- 3x size: `image@3x.png`

<!-- break -->

## Remote Images

Remote images are loaded via their URL, and must have a specific height/width set (otherwise they will not be visible):

``` jsx
// Source should be an object with a `uri` key
const source = {
  uri: 'http://lorempixel.com/300/150/'
};

const style = {
  height: 150,
  width: 300
};

return <Image source={source} style={style} />
```

<!-- break -->

## Buttons

A React Native button can be created with one of two components:

- `TouchableHighlight`
- `TouchableOpacity`

You are free to use many other components as a child of the `Touchable*` component, typically you would use `Text` and/or `Image`.

Add an `onPress` attribute to govern what happens when the button is pressed.

A `Button` component also exists, which is a thin wrapper around `TouchableHighlight`. Use `TouchableHighlight` instead, as it is more flexible.

<!-- break -->

### TouchableHighlight

A button which changes the colour of its background when it is tapped.

Often used for main 'call-to-action' type buttons, or tappable items in a list.

``` jsx
const styles = StyleSheet.create({
  button: { backgroundColor: '#0288D1', padding: 20 },
  label: { color: '#FFFFFF' }
});
return (
  <TouchableHighlight style={styles.button}
   underlayColor="#01579B" onPress={this.onPress}>
    <Text style={styles.label}>Press Me!</Text>
  </TouchableHighlight>
);
```

<!-- break -->

### TouchableOpacity

A button which lowers its opacity when it is tapped.

Often used for 'backgroundless' buttons, such as icon buttons in a header or tab bar.

``` jsx
import icon from './heart.png';
const styles = StyleSheet.create({
  icon: { height: 32, width: 32, margin: 10 }
});
return (
  <TouchableOpacity activeOpacity={0.5} onPress={this.onPress}>
    <Image style={styles.icon} source={icon} />
  </TouchableOpacity>
);
```

<!-- break -->

## Further Reading

- [View](http://www.reactnativeexpress.com/view)
- [Text](https://facebook.github.io/react-native/docs/text.html)
- [Styles](https://facebook.github.io/react-native/docs/style.html) and [StyleSheet](https://facebook.github.io/react-native/docs/stylesheet.html)
- [Flexbox](http://www.reactnativeexpress.com/flexbox)
- [Image](http://www.reactnativeexpress.com/image)
- [TouchableOpacity](https://facebook.github.io/react-native/docs/touchableopacity.html)
- [TouchableHighlight](https://facebook.github.io/react-native/docs/touchablehighlight.html)
- [ScrollView](http://www.reactnativeexpress.com/scrollview)
